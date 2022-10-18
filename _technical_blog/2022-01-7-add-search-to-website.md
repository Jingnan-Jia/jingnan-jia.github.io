---
title: 'Add search to your website'
tags:
  - Github
  - Website
  - Tutorial
  - Jekyll
---

As a technical blog, with the increasement of contents, it becomes difficult to remember all the things you have written 
down. Thast's why we need a `Search` function for our website.

Following [this blog](https://blog.webjeda.com/instant-jekyll-search/#why-a-jekyll-blog-needs-search-option) I started 
my journey.

As far as I know, there are several solutions:
1. Lunr
2. Google Custom Search Engine
3. Algolia
4. Simple Jekyll Search

As [Cristianpb](https://cristianpb.github.io/blog/jekyll-algolia) said:

>There are two ways to implement a search engine:

> 1. having a backend server that fetch the data and calculates the recommendation or
> 2. using a frontend application to filter data on the client side.
>
> The advantage of using a frontend application to filter data is the fact that you don’t need a backend service, so it works well with static sites. However, if your data is heavy, it may decrease the web navigation performance. A popular example of search engine on client side is lunr.js.
> 
> The backend service is then a more robust solution that can scale with your data. Some examples of engines that can be used for backend search engines are Apache SolR or Elasticsearch.
> 
> I wanted to have the advantages of both of them, having an scalable, fast and light search solution, so I decided to use Algolia search engine.

Inspired by him and after some survey, I decided to use Algolia. It is fast, instant, and free (in 10000 records). 
I followed part of [this blog](https://sujaykundu.com/blog/adding-real-time-search-to-jekyll-site-using-algolia/) and finished 
the following steps:
1. registered account on [Algolia](https://www.algolia.com/)
2. add the jekyll-algolia gem to your Gemfile
    ```python
    group :jekyll_plugins do
       gem 'jekyll-algolia', '~> 1.0'
    end
    ```
3. add algolia application settings in _config.yml file (this part is from [this blog](https://github.com/iBug/iBug-source/blob/master/_config.yml)):
    ```python
    search                   : true # true, false (default)
    search_full_content      : true # true, false (default)
    search_provider          : algolia # lunr (default), algolia, google
    algolia:
      application_id         : "14DZKASAEJ"
      index_name             : "iBug_website"
    # nodes_to_index         : 'section.page__content p, section.page__content h1, section.page__content h2, section.page__content h3, section.page__content h4, section.page__content h5, section.page__content h6, section.page__content img, section.page__content blockquote, section.page__content li, section.page__content dt, section.page__content dl'
      search_only_api_key    : "a0d8cb9da2d6ad0d17dcd40c58c72a56"
      powered_by             : true # true (default), false
      settings:
        searchableAttributes: ["title", "hierarchy.lvl0", "hierarchy.lvl1", "hierarchy.lvl2", "hierarchy.lvl3", "hierarchy.lvl4", "hierarchy.lvl5", "unordered(content)", "collection,categories,tags"]
        customRanking: ["desc(date)", "desc(weight.heading)", "asc(weight.position)"]
        attributesToHighlight: ["title", "hierarchy.lvl0", "hierarchy.lvl1", "hierarchy.lvl2", "hierarchy.lvl3", "hierarchy.lvl4", "hierarchy.lvl5", "content", "html", "collection", "categories", "tags"]
        attributesForFaceting: ["searchable(tags)", "searchable(type)", "searchable(title)"]
      files_to_exclude:
        - _pages/404.md
        - _pages/index.md
        - README.md
        - REMOTE_README.md
        - _home/status.html
        - _posts/2009/2009-11-13-regex-match-open-tags-except-xhtml-self-contained-tags.md
        - _posts/2021/2021-04-17-tunight-talk.md
    ```
4. Here I followed [Cristianph's blog](https://cristianpb.github.io/blog/jekyll-algolia) to continue the remaining steps.

