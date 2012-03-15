---
layout: post
title: "TIL The very, very long way"
guid: til-the-very-very-long-way
category:
tagline: ""
tags: ['rails']
---
{% include JB/setup %}

Whilst upgrading an application to Rails 3.1 recently I ran into one annoying heisenberg.

Long story short, do not use "stream" as a controller action name in 3.1 as it is used by the new HTTP streaming.