---
title: Testing a new shortcode
author: R package build
date: '2021-05-20'
slug: testing-a-new-shortcode
categories: []
tags: [hugo, youtube, shortcode, bail]
subtitle: ''
summary: ''
authors: []
lastmod: '2021-05-20T21:15:00-04:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Let's see if we can get [this shortcode](https://discourse.gohugo.io/t/howto-youtube-embed-with-custom-start-time/7060/6) working, which will allow us to embed a YouTube video with a start and end time.

Here is Chris Bail, introducing topic models, dropping some knowledge about setting explicit seeds for reproducible results. I want friends who do topic models.

{{< blogdown/youtubestartend IUAHUEy1V0Q 518 537 >}}

<br />

The shortcode file `youtubestartend.html` contains:

```html
<!-- https://discourse.gohugo.io/t/howto-youtube-embed-with-custom-start-time/7060/6 -->
<div style="position: relative; padding-bottom: 56.25%; padding-top: 30px; height: 0; overflow: hidden;">
    <iframe src="https://www.youtube-nocookie.com/embed/{{ index .Params 0 }}?start={{ index .Params 1 }}&end={{ index .Params 2}}"
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" allowfullscreen frameborder="0" title="YouTube Video"></iframe>
</div>
```

and is placed in the directory `layouts/shortcodes/blogdown/`. (**NOTE:** make sure the protocol is either `https` or `http` to match your hosting. If there's a mismatch, it won't work. We're all using https now, right?)

The embedded code, used above, is:

```r
{{</* blogdown/youtubestartend IUAHUEy1V0Q 518 539 */>}}
```

...and incidentally, the way you present the above code, without having the shortcode actually rendered by Hugo, is explained [in this Infinite Ink post](https://www.ii.com/hugo-tips-fragments/#_11_escaping_hugo_shortcodes). Basically, you put the entire shortcode between `/* C comment delimiters */`:

```r
{{</*/* blogdown/youtubestartend IUAHUEy1V0Q 518 539 */*/>}}
```

...and to render THAT text above, you have to do double delimiters:

```r
{{</*/*/* blogdown/youtubestartend IUAHUEy1V0Q 518 539 */*/*/>}}
```

...and so forth.
