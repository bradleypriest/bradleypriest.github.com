---
layout: post
title: "What's new in EmberJS #11"
guid: "whats-new-in-emberjs-11"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Some pretty big breaking changes again this week, part of being on the edge though, right.

###Weekly Wrapup #11

#### Breaking Changes

* In the [biggest change](https://github.com/emberjs/ember.js/pull/1176) of the week, `getPath/setPath` have been removed in favour of supporting full paths in `get` and `set`.

* As of [83b7a6](https://github.com/emberjs/ember.js/commit/83b7a61a892e55423cf1e66f606b13435bcab8f0) the `action` helper now requires an explicit context to be set. The api has also changed, the context is now simply passed as an optional second parameter. {{action edit context="post"}} becomes {{action edit post}}. If you were relying on default contexts you will need to use {{action edit this}}

#### Improvements

* PR [1044](https://github.com/emberjs/ember.js/pull/1044/) added `canInvoke` and `tryInvoke` methods to check and perform methods only if the target responds to them.

* PR [732](https://github.com/emberjs/ember.js/pull/732) adds the ability to provide a falsy option to Ember.View bindings.   e.g. `classNameBindings: ['isEnabled:enabled:disabled']`

* [396c08](https://github.com/emberjs/ember.js/commit/396c08b1322f4b642a65005cc89cdd7bb8acce06) adds the new `connectControllers` method to make other controllers available on the controller currently being used. `overviewController.connectControllers('person', 'post');` will let you do `controller.get('postController')` on the overviewController.

If anyone has worked out how to use jekyll syntax highlighting with handlebars brackets, please get in touch.

If I missed anything please let me know in the comments, twitter or IRC at #emberjs.