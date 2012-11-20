---
layout: post
title: "What's new in EmberJS #19"
guid: "whats-new-in-emberjs-19"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

###Weekly Wrapup #19

#### Breaking Changes

* [ed38ab](https://github.com/emberjs/ember.js/commit/ed38ab3777733597ac5abd33ce26c3edeb2d7d13) removes the deprecated defaulting of a view's context to itself, this may break some code samples around the place, but should not affect full applications.

#### Updates

* As of [PR 1393](https://github.com/emberjs/ember.js/pull/1393), `_super()` can now be called inside of computed properties.

* [PR 1504](https://github.com/emberjs/ember.js/pull/1504) adds an example of how to render a `CollectionView` with different childViews.

* [PR 1528](https://github.com/emberjs/ember.js/pull/1528) adds an `afterRender` queue for view rendering. A common use of this is to perform an action after all of a `CollectionView`'s children have been rendered.

* [PR 476](https://github.com/emberjs/data/pull/476) provides some initial error handling to ember-data. A 422 puts the record into an invalid state and sets an `errors` object onto the model. Any other server failure puts the object into an error state.

* [PR 422](https://github.com/emberjs/data/pull/422) reinstates the `RESTAdapter`'s default transforms.

* A conscious effort is being made to be format agnostic and not hardcode any method names/fields to JSON in ember-data, see [here](https://github.com/emberjs/data/commit/03739a7783de33b1ab1a89f3ecef236d7d3ba064). This shouldn't cause too many issues unless you are using a highly customized adapter.

#### Resources

* At the recent Ember meetup at [Addepar](https://addepar.com/) [Tom and Yehuda talked](https://addepar.com/ember/) about upcoming changes to the router and ember-data, worth a look.


If I missed anything please let me know in the comments, twitter or IRC at #emberjs.
