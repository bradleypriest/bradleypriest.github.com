---
layout: post
title: Simple Rails Snippets
guid: simple-rails-snippets
tagline:
category:
tags: ['rails']
---

<p>There has been a bit of development around content micro-management in the Rails ecosystem lately.</p>

<p>Thoughtbot just released their hosted service <a href="http://www.copycopter.com">Copycopter</a>. Quickleft brought out the <a href="http://www.github.com/quickleft/regulate">Regulate</a> gem.</p>

<p>It’s really good to see some simple solutions to what should really be a simple problem.</p>

<p>For me, even these seem a bit much, if you just want to add really basic snippet management it really isn’t that hard to from scratch. I can’t promise you this is the best way to do it, but it works well for me, comments are greatly appreciated.</p>

<p>Start by creating a new Snippet model. I’m just going to use <a href="http://www.railscasts.com">Ryan Bates’</a> amazing <a href="http://www.github.com/ryanb/nifty-generators">nifty-generators</a>. All you really need is a name and content. I’m throwing in a status for drafts as well.</p>

<pre class="prettyprint"><code>$ rails generate nifty:scaffold Snippet title:string snippet:text status:string</code></pre>

<p>Now let’s set up the basics: A simple helper</p>

<p><em>snippet_helper.rb</em></p>

<pre class="prettyprint"><code class="language-ruby">def snippet_for(name, default = nil)

  Rails.cache.fetch("snippet::"+name.to_s)) do

    Snippet.published.find_by_title(name.to_s) || default || "Snippet for #{name.to_s} missing"

  end

end



alias_method :s, :snippet_for

</code></pre>

<p>In the snippet helper I’m defining a snippet_for method:</p>

<p>This takes the name of the snippet, and an optional default value. Make sure you use descriptive names here, you’ll thank yourself later.</p>

<p>The helper will try to find a value first by searching the rails cache, followed by the snippet database, followed by the optional default and lastly will show a snippet not found message.</p>

<p>In the last line I'm aliasing snippet_for(…) to s(..) just for brevity</p>

<p><em>models/snippet.rb</em></p>

<pre class="prettyprint"><code class="language-ruby">class Snippet < ActiveModel

  after_save :clear_cache

  scope :published where(:status => 'published')



  def to_s

    snippet

  end



  def clear_cache

    Rails.cache.delete("snippet::"+title)

  end

end

</code></pre>

<p>The snippet model contains a simple published scope. And an after_save callback to allow for snippet updating. If you starting enhancing your snippet model you’ll probably want to implement a Rails sweeper.</p>

<p>Now in your code when you need a snippet</p>

<pre class="prettyprint"><code class="language-ruby">  = snippet_for(:call_to_action, 'Click Me')

  = s(:call_to_action, 'Click Me')</code></pre>
