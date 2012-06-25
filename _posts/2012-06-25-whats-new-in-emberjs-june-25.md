---
layout: post
title: "What's new in EmberJS #8"
guid: "whats-new-in-emberjs-june-25"
category:
tags: []
---
{% include JB/setup %}

Not so much new code this week, but the documentation is making leaps and bounds

###Weekly Wrapup #8

#### Breaking Changes

* [d23ea3](https://github.com/emberjs/ember.js/commit/d23ea3ab501fc0e8f591a793b927f572436647a1) changes `app.stateManager` to `app.router`

#### Improvements

* One of the last major bugs in the new router has a [PR](https://github.com/emberjs/ember.js/pull/1059) for a fix.

* [37d331](https://github.com/emberjs/data/commit/37d3319360be4e8f242a39111290a844720af3ab) ember-data now gives the store to each controller.

* In ember-data the ManyArray now provides a `isLoaded` flag [f707b6c](https://github.com/emberjs/data/commit/f707b6c4868e589c355ad25f1c0d54914f916e72)

If I missed anything please let me know in the comments or on twitter.