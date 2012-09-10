---
layout: post
title: "What's new in EmberJS #14"
guid: "whats-new-in-emberjs-14"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Been a bit quiet on github these last couple of weeks, I guess everyone's got to do some real work sometimes. Still plenty of bug fixes and features being put together by the rest of the community though, which is good to see

###Weekly Wrapup #14

#### Updates

* [9ecb570](https://github.com/emberjs/ember.js/commit/9ecb57019f0ba705bcc67aa59d01a3816e7bbfa4) adds `currentPath` to `Ember.StateManager` and therefore the router as shorthand for calling `currentState.path`

* [PR 1330](https://github.com/emberjs/ember.js/issues/1330) cleans up some issues with Ember.onerror in some browsers.

* Lots of documentation [has](https://github.com/emberjs/ember.js/commit/bad53798ac5e3efad2069beeae0248c5fcf99ebc) [been](https://github.com/emberjs/ember.js/commit/479e598eaea64f6714b8a4619e8cb5ca87ccc6a5) [added](https://github.com/emberjs/ember.js/commit/430c2b6960168b349e0e13a70145638e0eeea403) to the core `Ember.Application` which should hopefully start to clear the basics up.


#### Articles

* trek has put together what is probably the best [Intro to EmberJS](http://trek.github.com) article I've seen. It's worth a read even if you're an Ember pro.

* [Ember Handlebars Helpers, Bound and Unbound](http://techblog.fundinggates.com/blog/2012/08/ember-handlebars-helpers-bound-and-unbound/) from joliss.  
I personally had been using [this gist](https://gist.github.com/3362086) up until now, but this looks like a cleaner alternative until [PR 1274](https://github.com/emberjs/ember.js/pull/1274) gets merged.


If I missed anything please let me know in the comments, twitter or IRC at #emberjs.
