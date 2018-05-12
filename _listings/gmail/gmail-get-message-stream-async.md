---
version: 1.2.0
info:
  title: Gmail
  version: 1.2.0
servers:
- url: www.googleapis.com/{userId}/messages
  scheme: https
  asyncapi_servers_variables:
    userId:
      description: The user's email address. The special value me can be used to indicate
        the authenticated user.
    includeSpamTrash:
      description: Include messages from SPAM and TRASH in the results.
    labelIds:
      description: Only return messages with labels that match all of the specified
        label IDs.
    maxResults:
      description: Maximum number of messages to return.
    pageToken:
      description: Page token to retrieve a specific page of results in the list.
    q:
      description: 'Only return messages matching the specified query. Supports the
        same query format as the Gmail search box. For example, "from:someuser@example.com
        rfc822msgid: is:unread". Parameter cannot be used when accessing the api using
        the gmail.metadata scope.'
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/{userId}_messages'
---