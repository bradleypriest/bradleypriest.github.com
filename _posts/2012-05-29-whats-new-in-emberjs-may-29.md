---
layout: post
title: "What's new in EmberJS May 29"
guid: "whats-new-in-emberjs-may-29"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Lots and lots of work on the master branch this week to do with routing. It's getting better every day

###Weekly Wrapup #4

* As of [d1fd4e](https://github.com/emberjs/ember.js/commit/d1fd4ec850b0b32f21a51068a56c318478bf6632) Handlebars is not bundled with Ember, if you're not already using it in your application you'll be told about it. And if you're using rails the ember-rails gem includes it for you anyway.

* [10f7ab](https://github.com/emberjs/ember.js/commit/10f7ab46a7cc553d4e120693b2b26acd8be73fa5) introduces Ember.ObjectProxy and some Ember.ObjectController sugar

* Routing changes include adding [redirectsTo](https://github.com/emberjs/ember.js/commit/91a8975b8d3a0b873b421f1dbc4ea41f92c92bc2)

* The router now initializes at a [root state](https://github.com/emberjs/ember.js/commit/7b15026577f1efee02f2a90e2f560094b2d508c7).

* `goToState` has been replaced by `transitionTo` in statemanagers

* setupContext/setupControllers has been renamed `connectOutlets`

* The \{\{outlet}} helper has been added. Check out [this file](https://github.com/emberjs/ember.js/blob/master/packages/ember-handlebars/lib/helpers/outlet.js) for details. This gives the ability for a controller to fill in the currentView for a given area.

* In [PR #268](https://github.com/emberjs/data/pull/268) a new Errors object has been proposed for ember-data, designed to plug and play with Rails

If I missed anything please let me know in the comments or on twitter.