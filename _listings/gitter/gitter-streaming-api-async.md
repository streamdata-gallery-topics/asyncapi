---
version: 1.2.0
x-collection-name: Gitter
info:
  title: Gitter Streaming API
  version: 1.2.0
servers:
- url: https://stream.gitter.im/v1/rooms/{roomId}/{resource}
  scheme: https
  schemeVersion: "1.1"
  asyncapi_servers_variables:
    roomId:
      description: Id of the Gitter room.
    resource:
      description: The resource to consume.
stream:
  framing:
    type: chunked
    delimiter: \r\n
  read:
  - $ref: '#/components/messages/chatMessage'
  - $ref: '#/components/messages/heartbeat'
components:
  messages:
    chatMessage:
      summary: A message represents an individual chat message sent to a room. They
        are a sub-resource of a room.
      payload:
        properties:
          id:
            type: string
            description: ID of the message.
          text:
            type: string
            description: Original message in plain-text/markdown.
          html:
            type: string
            description: HTML formatted message.
          sent:
            type: string
            description: ISO formatted date of the message.
    fromUser:
      summary: User that sent the message.
      payload:
        properties:
          id:
            type: string
            description: Gitter User ID.
          username:
            type: string
            description: Gitter/GitHub username.
          displayName:
            type: string
            description: Gitter/GitHub user real name.
          url:
            type: string
            description: Path to the user on Gitter.
          avatarUrl:
            type: string
            description: User avatar URI.
          avatarUrlSmall:
            type: string
            description: User avatar URI (small).
          avatarUrlMedium:
            type: string
            description: User avatar URI (medium).
          v:
            type: number
            description: Version.
          gv:
            type: string
            description: Stands for "Gravatar version" and is used for cache busting.
          unread:
            type: boolean
            description: Boolean that indicates if the current user has read the message.
          readBy:
            type: number
            description: Number of users that have read the message.
    urls:
      summary: List of URLs present in the message.
    mentions:
      summary: List of @Mentions in the message.
      payload:
        properties:
          screenName:
            type: string
            description: ""
          userId:
            type: string
            description: ""
    issues:
      summary: 'List of #Issues referenced in the message.'
      payload:
        properties:
          number:
            type: string
            description: ""
    meta:
      summary: Metadata. This is currently not used for anything.
      payload:
        properties:
          v:
            type: number
            description: Version.
          gv:
            type: string
            description: Stands for "Gravatar version" and is used for cache busting.
    heartbeat:
      summary: Its purpose is to keep the connection alive.
---