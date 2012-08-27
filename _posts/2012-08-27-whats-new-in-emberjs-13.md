---
layout: post
title: "What's new in EmberJS #13"
guid: "whats-new-in-emberjs-13"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

###Weekly Wrapup #13

Most of the work at the moment seems to be in the refactoring of ember-data. It's not in master yet, but expect some pretty big changes. There's also a lot of work going on in the documentation side, if you find something amiss please help the core team out.

#### Breaking changes

* [ba3e74](https://github.com/emberjs/ember.js/commit/ba3e74e02d160fa870181a851c9e897fc66e4b6c) updated the application set up process, this should be seamless for most people, but make sure your app is calling `initialize`.

#### Updates

* [933b2b](https://github.com/emberjs/ember.js/commit/933b2b4a6eb4f82884c4ec5c567890ffb458beab) adds a `disconnectOutlet` method. AFAICT this is only useful for very specific usecases as Ember handles normal view management for you.

* The awesome ember-bootstrap project has moved. You can find it at it's new home at [https://github.com/emberjs-addons/ember-bootstrap](https://github.com/emberjs-addons/ember-bootstrap)

#### Articles

There's a great article on the current state of routing over on [dagda1's blog](http://www.thesoftwaresimpleton.com/blog/2012/08/20/routing_update/)



If I missed anything please let me know in the comments, twitter or IRC at #emberjs.