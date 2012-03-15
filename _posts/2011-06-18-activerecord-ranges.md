---
layout: post
title: ActiveRecord Ranges
guid: activerecord-ranges
category:
tagline:
tags: ['rails','active_record']
---
{% include JB/setup %}

Just a quick one today, I'm going to mention a quick trick you may have heard about, but is definitely worth knowing.

When using ActiveRecord as well as passing a String/Integer or Array into a query you can also use a Range.

I find this particularly helpful when searching by date.

For example instead of:

{% highlight ruby %}
  Widget.where('created_at > ? AND created_at < ?', 2.hours.ago, Time.now)
    #=> SELECT "widgets".* FROM "widgets" WHERE (created_at > '2011-06-18 03:38:58.493361' AND created_at < '2011-06-18 05:38:58.493442')
{% endhighlight %}

You can use a range, e.g.

{% highlight ruby %}
  Widget.where(:created_at => 2.hours.ago..Time.now)
    #=> SELECT "widgets".* FROM "widgets" WHERE ("widgets"."created_at" BETWEEN '2011-06-18 03:36:53.551349' AND '2011-06-18 05:36:53.551489')
{% endhighlight %}

Notice how using an inclusive range produces a SQL BETWEEN query.

Using an exclusive range gives a different query.

{% highlight ruby %}
  Widget.where(:created_at => 2.hours.ago...Time.now)
    #=> SELECT "widgets".* FROM "widgets" WHERE ("widgets"."created_at" >= '2011-06-11 05:25:12.738961' AND "widgets"."created_at" < '2011-06-18 05:25:12.739321')
{% endhighlight %}

Use carefully.

For an interesting use of this check out one of the new methods added to Rails 3.1 check out Date.today.all_day added [here](https://github.com/rails/rails/blob/master/activesupport/lib/active_support/core_ext/time/calculations.rb#L251-274).
