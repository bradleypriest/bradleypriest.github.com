---
layout: post
title: "What's new in EmberJS May 14"
guid: "whats-new-in-emberjs-may-14"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Not too many changes to master this week, but looks like baked-in routing might be just around the corner.

###Weekly Wrapup #2

* [Routing](https://github.com/emberjs/ember.js/commits/routing): There's been a bit of action on the routing branch in the last few days, and it's looking really good, check out a description from wycats [here](https://gist.github.com/2679013).

* There's a bit of a discussion going on [here](https://github.com/emberjs/ember.js/pull/803) on implementing a SortedArrayProxy into core.

* ghempton's [route-manager](https://github.com/ghempton/ember-routemanager) got some cleaning up, it now generates hashbang URLs when pushState is off and has fixed the initial page load render bug.

* Ember data has a couple of [pull](https://github.com/emberjs/data/pull/253) [requests](https://github.com/emberjs/data/pull/252) fixing a couple of bugs with parent-child relationships. With these changes creating a parent and it's children in one transaction doesn't lose the children.

If I missed anything please let me know in the comments or on twitter.