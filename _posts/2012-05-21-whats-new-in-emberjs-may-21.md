---
layout: post
title: "What's new in EmberJS May 21"
guid: "whats-new-in-emberjs-may-21"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

EmberJS 0.9.8 just released with a shiny new website. Check it out [http://emberjs.com](http://emberjs.com).

###Weekly Wrapup #3

* EmberJS 0.9.8 just released, check out the [changelog](https://github.com/emberjs/ember.js/blob/master/CHANGELOG).

* Most importantly routing is now built right in to core, check out a couple of blog posts about it [here](https://gist.github.com/2679013), [here](http://tomdale.net/2012/05/ember-routing/) and [here](https://gist.github.com/2728699). Beware it's not 100% finished, but its pretty close.

* Bindings being cacheable by default and views reserving context are now on by default. If you're not ready to change yet, set ENV.CP_DEFAULT_CACHEABLE = false or ENV.VIEW_PRESERVES_CONTEXT = false to change them back, but beware the option is being removed with the 1.1 release.

* The handlebars [action](https://github.com/emberjs/ember.js/commit/cdfb4673c80c17203f940f9c2087661a9116880a) helper now takes a context argument to pass instead of the jQuery event.

If I missed anything please let me know in the comments or on twitter.