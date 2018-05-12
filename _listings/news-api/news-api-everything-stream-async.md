---
version: 1.2.0
info:
  title: News API
  version: 1.2.0
servers:
- url: newsapi.orgeverything/
  scheme: https
  asyncapi_servers_variables:
    q:
      description: Keywords or phrases to search for.
    sources:
      description: A comma-seperated string of identifiers (maximum 20) for the news
        sources or blogs you want headlines from. Use the /sources endpoint to locate
        these programmatically or look at the sources index.
    domains:
      description: A comma-seperated string of domains (eg bbc.co.uk, techcrunch.com,
        engadget.com) to restrict the search to.
    pageSize:
      description: The number of results to return per page. 20 is the default, 100
        is the maximum.
    page:
      description: Use this to page through the results.
    apiKey:
      description: Your API key. Alternatively you can provide this via the X-Api-Key
        HTTP header.
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/everything_'
---