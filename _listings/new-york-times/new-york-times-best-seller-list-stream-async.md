---
version: 1.2.0
info:
  title: New York Times
  version: 1.2.0
servers:
- url: api.nytimes.com/books/v2/lists.{format}
  scheme: https
  asyncapi_servers_variables:
    list:
      description: |-
        The name of the Times best-seller list. To get valid values, use a list names request.

        Be sure to replace spaces with hyphens (e.g., e-book-fiction or hardcover-fiction, not E-Book Fiction or Hardcover Fiction). (The parameter is not case sensitive.)
    weeks-on-list:
      description: The number of weeks that the best seller has been on list-name,
        as of bestsellers-date
    bestsellers-date:
      description: |-
        YYYY-MM-DD

        The week-ending date for the sales reflected on list-name. Times best-seller lists are compiled using available book sale data. The bestsellers-date may be significantly earlier than published-date. For additional information, see the explanation at the bottom of any best-seller list page on NYTimes.com (example: Hardcover Fiction, published Dec. 5 but reflecting sales to Nov. 29).
    date:
      description: YYYY-MM-DD  The date the best-seller list was published on NYTimes.com
        (compare bestsellers-date)
    isbn:
      description: International Standard Book Number, 10 or 13 digits
    published-date:
      description: |-
        YYYY-MM-DD

        The date the best-seller list was published on NYTimes.com (compare bestsellers-date)
    rank:
      description: The rank of the best seller on list-name as of bestsellers-date
    rank-last-week:
      description: The rank of the best seller on list-name one week prior to bestsellers-date
    offset:
      description: Sets the starting point of the result set
    sort-order:
      description: Sets the sort order of the result set
    format:
      description: The format.
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/books_v2_lists_{format}'
---