---
layout: post
title: "What's new in EmberJS #10"
guid: "whats-new-in-emberjs-10"
category:
tags: [emberjs, ember-wrapup]
---
{% include JB/setup %}

Sorry I missed last week, but literally nothing had happened.
This week, there have been some massive changes under the hood.

###Weekly Wrapup #9

#### Improvements

* The [simplify-properties](https://github.com/emberjs/ember.js/tree/simplify-properties) branch was merged into master, this brings some sorely needed readability for us commonfolk for how the inner workings of property handling works.

* ember-data has a vastly improved [FixtureAdapter](https://github.com/emberjs/data/commit/0e81ecfc071a9e1703ad7ad3de00aca66265b4b7)

* A new `recordIsLoaded` method was added to data in [b63b84](https://github.com/emberjs/data/commit/b63b84b07d203e4467df034a1c19c37de20648a2)

* `connectOutlet` has been given [another syntax](https://github.com/emberjs/ember.js/commit/809746b05cc7fc3c278596a60dfbcb3e8b384348) (outletName, name, context) to make it easier to use custom outlet names. As always the options hash is still available if you need to use custom combinations.

* [d77a0c](https://github.com/emberjs/ember.js/commit/d77a0cf69de505104290874fedc1224b8a77b53c) adds the option to add a non standard `rootUrl` to the router.

* [e66827](https://github.com/wagenet/ember.js/commit/e668276a3aab382e145c3bc7afd059a9a6438534) meta clicks are now properly respected.

If I missed anything please let me know in the comments, twitter or IRC at #emberjs.