---
layout: post
title:  "Test of this gallery css"
categories: jekyll test
katex: True
---

This is a test; this is only a test

{% assign filenames = "pappus-1.png,pappus-2.png" | split: "," %}
{% include gallery.html %}