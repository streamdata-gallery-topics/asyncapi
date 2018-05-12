---
version: 1.2.0
info:
  title: New York Times
  version: 1.2.0
servers:
- url: api.nytimes.com/movies/v2/reviews/search.json
  scheme: https
  asyncapi_servers_variables:
    query:
      description: "Search keywords; matches movie title and indexed terms\n\nTo limit
        your search to exact matches only, surround your search string with single
        quotation marks (e.g., query='28+days+later'). Otherwise, responses will include
        partial matches (\"head words\") as well as exact matches (e.g., president
        will match president, presidents and presidential).\n  \n  If you specify
        multiple terms without quotation marks, they will be combined in an OR search.\n
        \ \n  If you omit the query parameter, your request will be equivalent to
        a reviews and NYT Critics' Picks request.\n"
    critics-pick:
      description: |
        Set this parameter to Y to limit the results to NYT Critics' Picks. To get only those movies that have not been highlighted by Times critics, specify critics-pick=N. (To get all reviews regardless of critics-pick status, simply omit this parameter.)
    reviewer:
      description: |
        Include this parameter to limit your results to reviews by a specific critic. Reviewer names should be formatted like this: Manohla Dargis.
    publication-date:
      description: |
        Single date: YYYY-MM-DD

        Start and end date: YYYY-MM-DD;YYYY-MM-DD

        The publication-date is the date the review was first published in The Times.
    opening-date:
      description: |
        Single date: YYYY-MM-DD

        Start and end date: YYYY-MM-DD;YYYY-MM-DD

        The opening-date is the date the movie's opening date in the New York region.
    offset:
      description: Positive integer, multiple of 20
    order:
      description: |
        Sets the sort order of the results.

        Results ordered by-title are in ascending alphabetical order. Results ordered by one of the date parameters are in reverse chronological order.

        If you do not specify a sort order, the results will be ordered by publication-date.
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/movies_v2_reviews_search_json'
---