---
version: 1.2.0
x-collection-name: IEX
info:
  title: IEX Delayed Quote (stream)
  version: 1.2.0
  description: This is a streaming API that has been autogenerated from the IEX using
    Streamdata.io.
servers:
- url: api.iextrading.com/stock/{symbol}/delayed-quote
  scheme: https
  asyncapi_servers_variables:
    symbol:
      description: Stock ticker symbol.
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/stock_{symbol}_delayed-quote'
---