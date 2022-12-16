# Caching in web

> The process of copying data from slower memory to faster memory is called caching.

Caching is used in many corners of computer science. from operation systems to networks.

## In front-end development

in context of frontend development it usually means memorizing server's response so that the next time data is needed, we can access it without making another request. it is specially useful when used with SPA frameworks and client side routing.

## In back-end development

In back-end we cache resources that are used often but rarely altered. for example landing pages, repetitive queries with same response etc.

CDNs and in-memory databases such as Redis are often use for caching in the back-end

## Cache consistency

One of the main problems with caching is keeping the copy and source in sync. This is the main reason that we shouldn't cache everything. Before caching we need to make sure of two things:

- Is optimization even needed? is the gained performance worth it?
- Will the source be changing quite often? is caching performance gain enough to breakeven with syncing overhead?
