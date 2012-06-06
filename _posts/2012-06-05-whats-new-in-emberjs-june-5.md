---
layout: post
title: "What's new in EmberJS June 5"
guid: "whats-new-in-emberjs-june-5"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Again mostly routing stuff this week, although it's great to see a lot of work being done on documentation.

###Weekly Wrapup #5

* [82d35e](https://github.com/emberjs/ember-rails/commit/82d35eb582d4a0a73613bba61b92613484a03a62)The ember-rails gem now generates the relevant ember resources when `rails g resource` is run

* Removed deprecated use of ["*"](https://github.com/emberjs/ember.js/commit/50d66622e551d0b98dcce80d12a9a8cd0541a873) and [leading periods](https://github.com/emberjs/ember.js/commit/bf9400510f00a2962bb36162eae642c56731a34a) in paths.

* As of [ee46ed](https://github.com/emberjs/ember.js/commit/ee46ed0a3bbde4f1b21e5b7d4a5550470a138a4e), views now inherit controllers from their parents.

* In one of the more controversial changes to Ember as of late, [7ae011](https://github.com/emberjs/ember.js/commit/7ae011753e595086287f06733028b260e0526847) removes binding transforms. Check out the comments for the recommended replacement.

* As of [7ff23e](https://github.com/emberjs/ember.js/commit/7ff23ee362b142f301b595e439afa964f3895b7c) routes should be handled better when using the back/forward buttons in the browser.

* A heroku app is now generating and uploading a new version of ember-latest after every push. You can now always get the latest version [here](https://github.com/emberjs/ember.js/downloads).

If I missed anything please let me know in the comments or on twitter.