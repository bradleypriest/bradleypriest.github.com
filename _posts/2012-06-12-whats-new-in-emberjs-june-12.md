---
layout: post
title: "What's new in EmberJS June 11"
guid: "whats-new-in-emberjs-june-11"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

A couple of new guides out this week and still plenty of docfixes and tidying up going on. I urge everyone to have read through the Ember source sometime if you haven't already.

###Weekly Wrapup #5

* Two new official guides have been released on [application structure/outlets](http://emberjs.com/guides/outlets/) and [asynchrony](http://emberjs.com/guides/asynchrony/). Check them out they're great for newbies and not-so-newbies alike.

* A new [Ember.Sortable](https://github.com/emberjs/ember.js/blob/master/packages/ember-runtime/lib/mixins/sortable.js) mixin has been added and is mixed in to ArrayProxy by default. To use add a `sortProperties` value to the Array and use `arrangedContent` to get the sorted values.

* [pushState](https://github.com/emberjs/ember.js/pull/945) and [none](https://github.com/emberjs/ember.js/pull/935) locations have been added to the router to complement the existing hash implementation.

* [871042](https://github.com/emberjs/ember.js/commit/871042a0d7083c9f5c5b6258fb0a84af814c34dd) moves dom events to use Ember's internal event system. This has the side-effect that returning false from a method should now stop propagation.

* A couple of IE related bugs were squashed

If I missed anything please let me know in the comments or on twitter.