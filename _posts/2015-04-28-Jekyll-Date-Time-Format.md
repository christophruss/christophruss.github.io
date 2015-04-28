---
layout: post
title: Jekyll Date Time Format
date: 2015-04-28 13:34:00 +0002
---

I recently discovered Jekyll (as you can see) and was wondering how to provide more detailed time and date information with a post.
Turns out, it is fairly easy, but not documented well enough. I initially only found this:

[http://jekyllrb.com/docs/frontmatter/](http://jekyllrb.com/docs/frontmatter/)

[http://stackoverflow.com/questions/18362317/what-is-the-expected-date-format-in-the-yaml-frontmatter-of-a-post-in-jekyll](http://stackoverflow.com/questions/18362317/what-is-the-expected-date-format-in-the-yaml-frontmatter-of-a-post-in-jekyll)

In essence you can (optionally) include a section `date: YYYY-MM-DD HH:MM:SS +/-TTTT` into the posts header.
It becomes more interesting, once you try to use that information. For example you RSS feed will initially assume your post was written at midnight (00:00:00).
With the `date: ` tag, this changes to the time you actually specified. To display the date an time, you can edit the layout of your post inside `_layouts/post.html`

Examples:

`Written on {{ page.date | date: "%e. %B %Y" }}`

`Written on {{ page.date | date: "%e. %B %Y" at %H:%M:%S %Z}}`

Now all we need to know is what all these `%VARIABLES` actually mean.

`%p` is PM
`%z` is time zone offset
`%Z` is time zone shortcut.

What I couldn't figure out is why the specified time-zone for a post is displayed correctly on the RSS feed, but not through the post layout.
