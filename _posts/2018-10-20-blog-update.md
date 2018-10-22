---
title: "Blog Update"
layout: post
tags: [Misc]
category: blog
description: Update the blog, test mathjax.
---

It has been almost exactly two years since I updated my personal website. 
There are a number of reasons I had wanted to do this:
1. I now regularly have a beard.
2. I have changed jobs and industries.
3. The goals of my personal website have changed.
4. The formatting of my website was breaking.
5. The format of my old website was no longer in line with what I consider a good personal site.
6. I want a more stable and professional personal email address.
7. I want multiple email addresses under the same domain.

(1) is obviously the most important. (_No but seriously, at least a few people have been confused and/or frightened by finding a picture of a beardless me._)

(2) is a topic about which I've been planning to blog, but see (4).

(3) is also a topic I'll also write about, but with fewer strong opinions than (2).

(4) was keeping me from posting because I wanted to fix the formatting first.

(5) meant that fixing (4) would be a lot of work, when I really also wanted a simpler layout.

(6) and (7) are both less about updating the site, and more about purchasing a domain. That's a different beast, but also gets filed under 'web-stuff-I'd-rather-put-off-forever' umbrella. My email address has a reference to my old career in it, which is now weird.

So, here's a first post on the updated site.

## Changes

Aside from the format garbling that was happening on my site, I didn't like the awkward side-by-side layout of posts, or the layout driven by a background image. I love big beautiful images, but I no longer wanted one as the core look of my personal website. I found the Jekyll Theme [Indigo](https://github.com/sergiokopplin/indigo) to be much more in line with what I was looking for.

### Tags

I modified a number of things. For one, on every other jekyll-based setup, the YAML header recognizes `tags: [a, list, of, tags]` to group blog posts by tag. In indigo, the line was `tag: ...` and posts that used the plural form would have the formatting of the tags botched. I fixed this by fixing a reference to `page.tag` in `_layouts/default.html` to `page.tags`. This seems to have fixed the problem, so now my old posts have their tags rendered correctly.

### Blog

All of my old posts didn't have a `category: blog` line in the YAML front matter. In order for them to show up on the list of blog posts on `mysiteurl.com/blog`, they now needed this. I added this line just after the `layout: post` line in all my posts by using this GNU sed command:

```sh
gsed -i '/layout: post/a category: blog/' _posts/*
```

## Math

I added support for MathJax so that math would render correctly. This is a \\( sin(x^2) \\) test of some $$x^2$$ math $$e=mc^2$$ in-line.

This part is single dollar signs:

$\Pr({A \mid B}) = \frac{\Pr({B \mid A}) \Pr(A)} {\Pr(B)}$

And this is with double dollar signs:

$$\Pr({A \mid B}) = \frac{\Pr({B \mid A}) \Pr(A)} {\Pr(B)}$$

$$J_\alpha(x) = \sum\limits_{m=0}^\infty \frac{(-1)^m}{m! \, \Gamma(m + \alpha + 1)}{\left({\frac{x}{2}}\right)}^{2 m + \alpha}$$



To get this to work, I added these lines to `_includes/default.html`, at the end of the `<head>` section:

```html
<!-- Mathjax Support -->
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      processEscapes: true
    }
  });
</script>

<script type="text/javascript"
    src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

```

Note that:
1. I didn't need to change anything about the markdown rendering engine. There is no `markdown: ...` line in my `_config.yml` file.
2. I didn't want to have to remember to type `mathjax: true` at the top of every post where I put an equation.
3. I found the solution here: https://tex.stackexchange.com/a/27656

## To Do

I'd eventually like to move the page from being hosted on GitHub's servers to another host. It looks like maybe cloudflare is good for that, but learning more about AWS is always on my to-do list.

I thought about adding a contact form, but I think having an email address specifically for web contact (e.g. hello@mywebsite.com) makes this moot.