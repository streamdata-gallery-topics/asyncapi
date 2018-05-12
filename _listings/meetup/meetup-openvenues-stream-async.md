---
version: 1.2.0
info:
  title: Meetup
  version: 1.2.0
servers:
- url: api.meetup.com/2/open_venues
  scheme: https
  asyncapi_servers_variables:
    lat:
      description: A valid latitude, limits the returned venues to those within radius
        miles
    state:
      description: For the US, a valid 2 character state code
    text:
      description: Venues that contain the given term or terms somewhere in their
        content. Separate terms with " AND " for venues that have combined terms.
        Append a trailing * to treat this as a prefix search
    zip:
      description: A valid US zip code, limits the returned venues to those within
        radius miles
    country:
      description: A valid country code.
    lon:
      description: A valid longitude, limits the returned venues to those within radius
        miles
    group_urlname:
      description: Returns venues with location relative to the group associated with
        this urlname
    city:
      description: A valid city
    radius:
      description: Radius, in miles for geographic requests, default 25.0 -- maximum
        100.0
    fields:
      description: Request that additional fields (separated by commas) be included
        in the output
    since_mtime:
      description: Return recent open venues with an mtime greater then the supplied
        time, in milliseconds since the epoch
    since_count:
      description: Request that some number of recent messages be sent immediately,
        if available. May not be specified in the same request as since_mtime.
    api_version:
      description: "2"
    trickle:
      description: When supplied with a request, the Meetup API will push your client
        the entire Meetup database of public venues in batches of 512
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/2_open_venues'
---