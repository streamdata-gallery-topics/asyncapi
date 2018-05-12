---
version: 1.2.0
info:
  title: Disqus
  version: 1.2.0
servers:
- url: disqus.com/threads/list.json
  scheme: https
  asyncapi_servers_variables:
    category:
      description: Defaults to null                         Looks up a category by
        ID
    forum:
      description: Defaults to null                         Looks up a forum by ID
        (aka short name)
    thread:
      description: Defaults to null                         Looks up a thread by ID
        You may pass us the &#39;ident&#39; query type instead of an ID by including
        &#39;forum&#39;. You may pass us the &#39;link&#39; query type to filter by
        URL. You must pass the &#39;forum&#39; if you do not have the Pro API Access
        addon.
    author:
      description: Defaults to null                         Looks up a user by ID
        You may look up a user by username using the &#39;username&#39; query type.
    since:
      description: Defaults to null                         Unix timestamp (or ISO
        datetime standard)
    related:
      description: 'Defaults to []                         You may specify relations
        to include with your response. Choices: forum, author, category'
    cursor:
      description: Defaults to null
    attach:
      description: 'Defaults to []                         Choices: topics'
    limit:
      description: Defaults to 25                         Maximum value of 100
    include:
      description: 'Defaults to [  open,  closed]                         Choices:
        open, closed, killed'
    order:
      description: 'Defaults to desc                         Choices: asc, desc'
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/threads_list_json'
---