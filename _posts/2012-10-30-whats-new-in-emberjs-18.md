---
layout: post
title: "What's new in EmberJS #18"
guid: "whats-new-in-emberjs-18"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Ember 1.0.0-pre.2 has been released, now with a semver compatible release number ;)

###Weekly Wrapup #18



#### Breaking Changes

* Ember-Data revision 7 is out, which changes how relationship changes are acknowledged check out [BREAKING_CHANGES](https://github.com/emberjs/data/blob/master/BREAKING_CHANGES.md) for details.

* A (currently) private mixin, `DS.Mappable`, has been introduced to implement per-type adapters, see the [commit](https://github.com/emberjs/data/commit/2609b8f1b6195e2545f6485c7097512765478b4f) and the [documentation](https://github.com/emberjs/data/commit/ca0ab37fbe9d0afdc896c7a8410e27cafabfb203)

#### Updates

* Ember 1.0.0-pre.2 released, check out the [blog post](http://emberjs.com/blog/2012/10/25/ember-1-0-pre2/) and the [changelog](https://github.com/emberjs/ember.js/blob/master/CHANGELOG)

#### N.B

* Explicitly missing from this post is mention of the [new router API](https://gist.github.com/3981133) being thrown around, I don't mean to bring personal preferences in, but I believe this is heading in the wrong direction. Currently getting started with the `Ember.Router` can be a bit of a hassle but I personally believe learning the philosophy behind the router/state-manager is the most important step in understanding Ember. Luckily it looks like the old API [won't be going anywhere](https://twitter.com/tomdale/status/263317907596013568).


If I missed anything please let me know in the comments, twitter or IRC at #emberjs.
