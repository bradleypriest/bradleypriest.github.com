---
layout: post
title: "What's new in EmberJS #16"
guid: "whats-new-in-emberjs-16"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Sorry guys and gals, it's been a couple of weeks since I last posted, been busy beta launching my new startup [TradeGecko](http://tradegecko.com), now back to the scheduled programming.

Lot's of big changes merged in the last few days, most newsworthy is the `relationships-improvements` branch of ember-data has been merged.

###Weekly Wrapup #16

#### Relationship Improvements

* The `relationships-improvements` branch of ember-data has been merged, this brings quite a few breakages along, particularly if you are modifying the defaults in any way.

* There's a lot to see here, so I suggest you take a look at the new documentation. I'll try and put together a migrating to ember-data V5 blog post in the next couple of weeks once I finish migrating my apps.

* If you have any outstanding issues PR's against ember-data please take the time to check they're still relevant and update them against the latest changes.


#### Updates

* [PR #1406](https://github.com/emberjs/ember.js/pull/1406) gives us an Ember.Deferred mixin which (almost, still WIP) implements the Promises/A spec.

* [PR #1354](https://github.com/emberjs/ember.js/pull/1354/) adds support for passing multiple contexts to events.

* [305202](https://github.com/emberjs/ember.js/commit/305202fa51aca55ce1ff935aa9fb8ebe3da4a0d4) removes the dependency on the browser `window`, this should make it easier for people using Ember with technologies like CommonJS and AMD. Check out the commit for details.

* [PR #1198](https://github.com/emberjs/ember.js/pull/1198) adds `presentCurrentView`, `dismissCurrentView`, `appendCurrentView` and `removeCurrentView` to Ember.ContainerView (and consequently outlets) for handling animations and so forth.

* [PR #1425](https://github.com/emberjs/ember.js/pull/1425) fixes an error with popstate on Chrome

* [945cd4](https://github.com/emberjs/ember.js/commit/945cd4a5a4f0851d9729385225ecd356f7f05ca5) no longer throws an error for Ember Apps without a router

* [134fc6](https://github.com/emberjs/ember.js/commit/134fc61b764ef5b464ab3ebef968716b7df5c50c) Ember now includes a basic instrumentation API.

* [PR #1449](https://github.com/emberjs/ember.js/pull/1449) allows toggling extending prototypes by object type.

* [PR #410](https://github.com/emberjs/data/pull/410) on ember-data changes the semantics of `findAll()` and adds an `all()` method which pretty much implements the old way.

#### Articles
* ghempton [explains how he integrates Analytics with Ember](http://codebrief.com/2012/10/ember-dot-js-analytics-integration/).
* tomdale giving a [talk on ember-data](http://www.youtube.com/watch?v=djhAsWGOImk) at last weeks Prague.js.

If I missed anything please let me know in the comments, twitter or IRC at #emberjs.
