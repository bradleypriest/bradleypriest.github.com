---
layout: post
title: "What's new in EmberJS #15"
guid: "whats-new-in-emberjs-15"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

There's a new documentation site up at [http://emberjs.com/api/](http://emberjs.com/api/). All of the documentation has been converted to YUIDoc for this move, so if you notice anything strange please send in a fix.

###Weekly Wrapup #15

#### Breaking Changes

* [bb149d](https://github.com/emberjs/ember.js/commit/bb149dcbb7df91866fce10e6dbec78c3e439d0ee) Removes support for inline anonymous templates

* [1c7cf46](https://github.com/emberjs/ember.js/commit/1c7cf46a866a545f68192ab588ee93a1ea160e00) Adds the `autoinit` flag to Application, no need to call `App.initialize` anymore unless you are doing something obscure.

#### Updates

* Handlebars 1.0-rc.1 has now been released.

* [PR 1310](https://github.com/emberjs/ember.js/pull/1310) The \{\{each\}\} helper now supports an `itemViewClass` for blockless use.

* [PR 1340](https://github.com/emberjs/ember.js/pull/1340/files) Injections can be specified the order to run before/after others.

* [PR 1317](https://github.com/emberjs/ember.js/pull/1317) The application initialization process has been refactored.

If I missed anything please let me know in the comments, twitter or IRC at #emberjs.
