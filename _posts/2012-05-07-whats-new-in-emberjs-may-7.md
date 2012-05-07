---
layout: post
title: "What's new in EmberJS May 7"
slug: "whats-new-in-emberjs-may-7"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

I am a huge Ember supporter. I have only been using the framework for 4 weeks now, but I am a complete convert. Hell, I'm building my new [startup](http://tradegecko.com) in it.

I don't have any cool libraries to share for it just yet, but in the meantime this is the least I can do.

###Weekly Wrapup #1

* [#00b894](https://github.com/emberjs/ember.js/commit/00b8940af1c948dd1974be184e022269a87a461d) updates ContainerView to optionally take a currentView object, which sets a single view inside the continer, great for statemanagers. (I currently use ember-layout, this commit may make that obsolete?)

* [#f96818](https://github.com/emberjs/ember.js/commit/f9681830b7385d2c85722c21409ae7c33da7dbee) Make it easy to inject controllers. I'm gonna be honest, I don't actually understand what's happening here, but it looks like they're working on some big updates.

* `each foo in bar` and `with foo as bar` handlebars helpers were added.

* A [whole](https://github.com/emberjs/ember.js/commit/09d7ad62b214c094621ade5515d2a29a59464f89) [lot](https://github.com/emberjs/ember.js/commit/fb0848b2d22e7325f59f89507cd4e855bdad9255) of [refactoring](https://github.com/emberjs/ember.js/commit/7e839f0fc32371c8776fc6da900a30a3e6906aa1) has been done to mutable array and enumerable to help speed things up.

* [PR #229](https://github.com/emberjs/data/pull/229) added the ability to rollback transactions to ember-data, both automatically and manually via `person.get('transaction').rollback()`.

* [PR #230](https://github.com/emberjs/data/pull/230) makes it easier to create child records e.g. `blog.get('posts').createRecord()`.

* [PR #236](https://github.com/emberjs/data/pull/236) fixes lifecycle events and makes `didCreate` and `didUpdate` fire correctly.

If I missed anything big please let me know in the comments or on twitter.

P.S. Thanks to [Mike Gunderloy](http://afreshcup.com/home/category/edge-rails) for the idea.