---
layout: post
title: Simple Rails Snippets
guid: simple-rails-snippets
tagline:
category:
tags: ['rails']
---
{% include JB/setup %}

There has been a bit of development around content micro-management in the Rails ecosystem lately.

Thoughtbot just released their hosted service [Copycopter](http://www.copycopter.com). Quickleft brought out the [Regulate](http://www.github.com/quickleft/regulate) gem.

It’s really good to see some simple solutions to what should really be a simple problem.

For me, even these seem a bit much, if you just want to add really basic snippet management it really isn’t that hard to from scratch. I can’t promise you this is the best way to do it, but it works well for me, comments are greatly appreciated.

Start by creating a new Snippet model. I’m just going to use [Ryan Bates’](http://www.railscasts.com) amazing [nifty-generators](http://www.github.com/ryanb/nifty-generators). All you really need is a name and content. I’m throwing in a status for drafts as well.

{% highlight bash %}
$ rails generate nifty:scaffold Snippet title:string snippet:text status:string
{% endhighlight %}

Now let’s set up the basics: A simple helper

*snippet_helper.rb*

{% highlight ruby %}
def snippet_for(name, default = nil)
  Rails.cache.fetch("snippet::"+name.to_s)) do
    Snippet.published.find_by_title(name.to_s) || default || "Snippet for #{name.to_s} missing"
  end
end

alias_method :s, :snippet_for
{% endhighlight %}

In the snippet helper I’m defining a snippet_for method:

This takes the name of the snippet, and an optional default value. Make sure you use descriptive names here, you’ll thank yourself later.

The helper will try to find a value first by searching the rails cache, followed by the snippet database, followed by the optional default and lastly will show a snippet not found message.

In the last line I'm aliasing snippet_for(…) to s(..) just for brevity

*models/snippet.rb*

{% highlight ruby %}
class Snippet < ActiveModel
  after_save :clear_cache
  scope :published where(:status => 'published')

  def to_s
    snippet
  end

  def clear_cache
    Rails.cache.delete("snippet::"+title)
  end
end
{% endhighlight %}

The snippet model contains a simple published scope. And an after_save callback to allow for snippet updating. If you starting enhancing your snippet model you’ll probably want to implement a Rails sweeper.

Now in your code when you need a snippet

{% highlight ruby %}
= snippet_for(:call_to_action, 'Click Me')
= s(:call_to_action, 'Click Me')
{% endhighlight %}
