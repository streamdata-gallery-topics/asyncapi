---
version: 1.2.0
info:
  title: LinkedIn
  version: 1.2.0
servers:
- url: api.linkedin.com/companies/
  scheme: https
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/companies_'
---