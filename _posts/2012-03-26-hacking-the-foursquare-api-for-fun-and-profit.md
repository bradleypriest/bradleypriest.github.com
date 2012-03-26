---
layout: post
title: "Hacking the Foursquare API for fun and profit??"
slug: "hacking-the-foursquare-api-for-fun-and-profit"
category:
tags: ['ruby']
---
{% include JB/setup %}

So I have a housemate who has a certain fascination with burgers. His favourite ones seem to come from the local BurgerFuel.

For 12 months he was the Foursquare mayor of Burgerfuel Parnel, eating lunch their every second day (healthy right!!). Luckily they had a great two for one deal for the mayor so he always had half price burgers.

However, after a 4 month OE surprisingly he was ousted. Now that he's back and into his habits again, it seems he just can't quite get the mayorship back.

So I thought I'd give him a bit of help.

Here's a quick little ruby script I wrote, use at your own risk, I can almost guarantee it's against their ToS.

<script src="https://gist.github.com/2204036.js?file=foursquare_bot.rb"> </script>

Firstly log in to Foursquare and head to [https://foursquare.com/oauth/](https://foursquare.com/oauth/) to register a new consumer.
You can fill in anything for the website and url, make sure to record the callback url though.

Run `FoursquareBot.get_oauth(client_id, callback_url)` to get a url to visit.
Open the url in your browser, authenticate with Foursquare and we're good to go, just copy down the code parameter from the url you get redirected to.

![URL](https://img.skitch.com/20120326-qia79s888pn5sdp8skn3trpqar.jpg)

Now you can checkin whenever you like with this one liner.

{% highlight ruby %}
  Foursquare.new(insert_client_id).checkin(your_location_id)
{% endhighlight %}

Next step is to make it a daemon and we're ready to go.