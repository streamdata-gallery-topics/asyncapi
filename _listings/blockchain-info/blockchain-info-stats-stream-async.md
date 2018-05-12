---
version: 1.2.0
info:
  title: Blockchain Info
  version: 1.2.0
servers:
- url: blockchain.info/stats
  scheme: https
  asyncapi_servers_variables:
    format:
      description: The format to return (json,html).
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/stats'
---