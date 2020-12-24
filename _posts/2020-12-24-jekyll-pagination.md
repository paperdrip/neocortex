---
layout: post
title: Add pagination to Jekyll site
date: 2020-12-24 07:45
tags: ["jekyll"]
summary: 
---
I have been using Jekyll to write my blog for quite sometime. The "so-simple-theme" takes care of all the layout and today, I try to add pagination to my site since I have enough entries now.

There are 3 things I need to do in enabling the page navigation bar

1. Include the following section in `_config.yml`

```
# Pagination - https://jekyllrb.com/docs/pagination/
paginate: 10
paginate_path: /page:num/

plugins:
  - jekyll-paginate

```

2. Include the pagination gem in `Gemfile`

```
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-paginate"
end
```

3. If you are using `index.md` for your layout, rename it to `index.html` with the following content

```
---
layout: home
excerpt: "Brain dump of an engineer with fading memory."
show_excerpts: true
paginate: true
entries_layout: list
---
```

The most important part would be the variable `paginate: true`. Rebuild the site and a nice navigation bar should be shown at the bottom of the page.

