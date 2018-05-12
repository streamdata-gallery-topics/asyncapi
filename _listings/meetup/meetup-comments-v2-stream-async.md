---
version: 1.2.0
info:
  title: Meetup
  version: 1.2.0
servers:
- url: api.meetup.com/2/event_comments
  scheme: https
  asyncapi_servers_variables:
    comment_id:
      description: Return comments for a given set of comment IDs, separated by commas
    member_id:
      description: Return comments for the given member_ids, separated by commas
    fields:
      description: Optionally accepts the value "member_photo" or "notifications"
    group_id:
      description: Return comments in groups with these ID numbers, separated by commas
    event_id:
      description: Return comments on these events, separated by commas.
    callback:
      description: |-
        Name of a function to be called with an array of Event Comment notification objects. If this
        parameter is not supplied, the chunked stream is joined instead.
    since_mtime:
      description: Should be supplied for all but the first polling request, so that
        any missed notifications are can be sent in an immediate response
    since_count:
      description: Request that some number of recent messages be sent immediately,
        if available. May not be specified in the same request as since_mtime.
    api_version:
      description: "2"
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/2_event_comments'
---