---
layout: post
title: "What's new in EmberJS #17"
guid: "whats-new-in-emberjs-17"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

It's been a good week for Ember updates, big thanks to Peter Wagenet for single-handedly reviewing and cleaning up [every single Ember ticket](https://twitter.com/wagenet/status/259510421814398976).

###Weekly Wrapup #16

#### Breaking Changes

* EmberJS now requires at least jQuery 1.7.2
* [ENV.VIEW_PRESERVES_CONTEXT](https://github.com/emberjs/ember.js/commit/710d1e1ab55a60edd259d8a3cd9c7467e1b50c41) & [ENV.CP_DEFAULT_CACHEABLE](https://github.com/emberjs/ember.js/commit/5ef55f22c584abc788fd98994af591f010ba82e9) flags have been removed.

#### Updates

* [PR #1406](https://github.com/emberjs/ember.js/pull/1459) changes the Ember.Deferred mixin to be Promises/A compatible by using RSVP.js.

* [PR #1465](https://github.com/emberjs/ember.js/pull/1465) adds support for globbed routes in the router.

* EmberJS now has a [CONTRIBUTING.md](https://github.com/emberjs/ember.js/blob/master/CONTRIBUTING.md) page. If you've ever felt like you've found a bug or wanted to know better how to help out, there's plenty of info there.

* [f103fe](https://github.com/emberjs/ember.js/commit/f103fe49de72c88c6c746e74ab0a500b51d35473) deprecates using \{\{collection\}\} without a class in favor of \{\{each\}\}.

* [PR #249](https://github.com/emberjs/data/pull/249) gives ember-data the ability to set a custom URL, just make sure you set up CORS properly.

#### Articles

* A new official guide has been added [Building Applications with Ember.js](http://emberjs.com/guides/router_primer/)

* James Croft runs through building a `FilterableMixin` for `Ember.ArrayProxy` [here](http://matchingnotes.com/ember-array-proxy/filterable-mixin).

If I missed anything please let me know in the comments, twitter or IRC at #emberjs.
