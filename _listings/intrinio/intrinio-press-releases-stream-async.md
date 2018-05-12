---
version: 1.2.0
info:
  title: Intrinio API
  version: 1.2.0
servers:
- url: api.intrinio.com/press_releases
  scheme: https
  asyncapi_servers_variables:
    identifier:
      description: ' the stock market ticker symbol associated with the company&rsquo;s
        common stock.  If the company is foreign, use the stock exchange code, followed
        by a colon, then the ticker.  You may request up to 10 tickers at once by
        separating them with a comma: '
    related:
      description: ' filter whether the list returned includes all press releases
        where a company is the subject or only press releases issued by the company:
        all | false | true'
    page_size:
      description: ' an integer greater than 1 for specifying the number of results
        on each page.'
    page_number:
      description: ' an integer greater than or equal to 1 for specifying the page
        number for the return values.'
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/press_releases'
---