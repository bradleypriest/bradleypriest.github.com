---
layout: post
title: "What's new in EmberJS June 18"
guid: "whats-new-in-emberjs-june-18"
category:
tags: []
---
{% include JB/setup %}

A couple of breaking changes this week, if you've been following master, there's a couple of quick tweaks that need to be made.

###Weekly Wrapup #5

#### Breaking Changes
* [d8383b](https://github.com/emberjs/ember.js/commit/d8383b65aaf9dcd0f92687b7ed6921f1a436a73c) creates an `Ember.Route` subclass of `Ember.State`, if you're using the new router, make sure you change over as there are currently no warnings.

* [be6939](https://github.com/emberjs/ember.js/commit/be69395f5eec4187b1df052d7386bcda45f79475) changes the arguments expected by `connectOutlet`. Check out the commit comment for details, but the basic change is that `connectOutlet` now takes a single string to define the View and Controller, removing the magic. If you need to customize further it can also take a hash of name, outletName, viewClass, controller and context.

* The \{\{action\}\} helper got some big changes. It now calls [stopPropagation](https://github.com/emberjs/ember.js/commit/aaa22a7ced26ec4cc079818b6a8991baed51d77a) and [preventDefault](https://github.com/emberjs/ember.js/commit/4b7b13f6f594a32b5abdc7419d22478f5f549328) automatically.

#### Improvements
* [2d26a36](https://github.com/emberjs/ember.js/commit/2d26a36f4119ffa0f8b41157dbb2856f27a33420) adds naïve route sorting. This fixes a [situation](https://github.com/emberjs/ember.js/pull/969) where a `:post_id` would always take precedence over a `new` segment. Now it sorts based on substrings, segment length and dynamicism.

* `Ember.Evented` now has [one](https://github.com/emberjs/ember.js/commit/1809e65012b93c0a530bfcb95eec22d972069745) method to add a one-time eventListener.

* `Ember.Evented` uses `trigger` instead of `fire` to keep in line with jQuery.

If I missed anything please let me know in the comments or on twitter.