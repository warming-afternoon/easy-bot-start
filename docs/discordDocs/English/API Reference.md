---
url: https://discord.com/developers/docs/reference
time: 2025-09-10P21:59:41
tags: 
---
# [API Reference](https://discord.com/developers/docs/reference#api-reference) 

On this page

Discord's API is based around two core layers , a HTTPS/REST API for general operations , and persistent secure WebSocket based connection for sending and subscribing to real-time events. The most common use case of the Discord API will be providing a service , or access to a platform through the [OAuth2](https://oauth.net/2/) API.

###### [Base URL](https://discord.com/developers/docs/reference#api-reference-base-url) 

```
https://discord.com/api
```

## API Versioning[](https://discord.com/developers/docs/reference#api-versioning) 

Some API and Gateway versions are now non-functioning , and are labeled as discontinued in the table below for posterity. Trying to use these versions will fail and return 400 Bad Request.

Discord exposes different versions of our API[](https://c.tenor.com/BuZl66EegkgAAAAC/westworld-dolores.gif) You should specify which version to use by including it in the request path like `https://discord.com/api/v{version_number}`

Omitting the version number from the route will route requests to the current default version (marked below) 

You can find the change log for the newest API version [here](https://discord.com/developers/docs/change-log) 

###### API Versions[](https://discord.com/developers/docs/reference#api-versioning-api-versions) 

<table><thead><tr><th>Version</th><th>Status</th><th>Default</th></tr></thead><tbody><tr><td>10</td><td>Available</td><td></td></tr><tr><td>9</td><td>Available</td><td></td></tr><tr><td>8</td><td>Deprecated</td><td></td></tr><tr><td>7</td><td>Deprecated</td><td></td></tr><tr><td>6</td><td>Deprecated</td><td>✓</td></tr><tr><td>5</td><td>Discontinued</td><td></td></tr><tr><td>4</td><td>Discontinued</td><td></td></tr><tr><td>3</td><td>Discontinued</td><td></td></tr></tbody></table>

## Error Messages[](https://discord.com/developers/docs/reference#error-messages) 

Starting in API v8 , we've improved error formatting in form error responses. The response will tell you which JSON key contains the error , the error code , and a human readable error message. We will be frequently adding new error messages , so a complete list of errors is not feasible and would be almost instantly out of date. Here are some examples instead:

###### Array Error[](https://discord.com/developers/docs/reference#error-messages-array-error) 

```
{
"code": 50035 , 
"errors": {
 "activities": {
  "0": {
  "platform": {
  "_errors": [
  {
  "code": "BASE_TYPE_CHOICES" , 
  "message": "Value must be one of ('desktop' , 'android' , 'ios') " 

  }
  ]
  } , 
  "type": {
  "_errors": [
  {
  "code": "BASE_TYPE_CHOICES" , 
  "message": "Value must be one of (0 , 1 , 2 , 3 , 4 , 5) " 

  }
  ]
  }
  }
 }
} , 
"message": "Invalid Form Body"
}
```

###### Object Error[](https://discord.com/developers/docs/reference#error-messages-object-error) 

```
{
"code": 50035 , 
"errors": {
 "access_token": {
  "_errors": [
  {
  "code": "BASE_TYPE_REQUIRED" , 
  "message": "This field is required"
  }
  ]
 }
} , 
"message": "Invalid Form Body"
}
```

###### Request Error[](https://discord.com/developers/docs/reference#error-messages-request-error) 

```
{
"code": 50035 , 
"message": "Invalid Form Body" , 
"errors": {
 "_errors": [
  {
  "code": "APPLICATION_COMMAND_TOO_LARGE" , 
  "message": "Command exceeds maximum size (8000) "
  }
 ]
}
}
```

## Authentication[](https://discord.com/developers/docs/reference#authentication) 

Authenticating with the Discord API can be done in one of two ways:

1. Using a bot token found on the Bot page within your app's settings. For more information on bots see [bots vs user accounts](https://discord.com/developers/docs/topics/oauth2#bot-vs-user-accounts) 

2. Using an OAuth2 bearer token gained through the [OAuth2 API](https://discord.com/developers/docs/topics/oauth2#oauth2) 

For all authentication types , authentication is performed with the `Authorization` HTTP header in the format `Authorization: TOKEN_TYPE TOKEN`

###### Example Bot Token Authorization Header[](https://discord.com/developers/docs/reference#authentication-example-bot-token-authorization-header) 

```
Authorization: Bot MTk4NjIyNDgzNDcxOTI1MjQ4.Cl2FMQ.ZnCjm1XVW7vRze4b7Cq4se7kKWs
```

###### Example Bearer Token Authorization Header[](https://discord.com/developers/docs/reference#authentication-example-bearer-token-authorization-header) 

```
Authorization: Bearer CZhtkLDpNYXgPH9Ml6shqh2OwykChw
```

## Encryption[](https://discord.com/developers/docs/reference#encryption) 

All HTTP-layer services and protocols (e.g. HTTP , WebSocket) within the Discord API are using TLS 1.2.

## Snowflakes[](https://discord.com/developers/docs/reference#snowflakes) 

Discord utilizes Twitter's [snowflake](https://github.com/twitter-archive/snowflake/tree/snowflake-2010) format for uniquely identifiable descriptors (IDs) 

These IDs are guaranteed to be unique across all of Discord , except in some unique scenarios in which child objects share their parent's ID. Because Snowflake IDs are up to 64 bits in size (e.g. a uint64) , they are always returned as strings in the HTTP API to prevent integer overflows in some languages. See [Gateway ETF/JSON](https://discord.com/developers/docs/events/gateway#encoding-and-compression) for more information regarding Gateway encoding.

###### Snowflake ID Broken Down in Binary[](https://discord.com/developers/docs/reference#snowflakes-snowflake-id-broken-down-in-binary) 


###### Snowflake ID Format Structure (Left to Right) [](https://discord.com/developers/docs/reference#snowflakes-snowflake-id-format-structure-left-to-right) 

<table><thead><tr><th>Field</th><th>Bits</th><th>Number of bits</th><th>Description</th><th>Retrieval</th></tr></thead><tbody><tr><td>Timestamp</td><td>63 to 22</td><td>42 bits</td><td>Milliseconds since Discord Epoch , the first second of 2015 or 1420070400000.</td><td><code> (snowflake &gt ; &gt ; 22) + 1420070400000</code></td></tr><tr><td>Internal worker ID</td><td>21 to 17</td><td>5 bits</td><td></td><td><code> (snowflake &amp ; 0x3E0000) &gt ; &gt ; 17</code></td></tr><tr><td>Internal process ID</td><td>16 to 12</td><td>5 bits</td><td></td><td><code> (snowflake &amp ; 0x1F000) &gt ; &gt ; 12</code></td></tr><tr><td>Increment</td><td>11 to 0</td><td>12 bits</td><td>For every ID that is generated on that process , this number is incremented</td><td><code>snowflake &amp ; 0xFFF</code></td></tr></tbody></table>

### Convert Snowflake to DateTime[](https://discord.com/developers/docs/reference#convert-snowflake-to-datetime) 

1759288472991170634194470579614620151057962016-04-30 11:18:25.796 UTC0000001001110001000001100101101011000001000000100000to binaryto decimalParse unix timestamp (ms) + 1420070400000Discord Epoch (unix timestamp in ms) Number of milliseconds since the Discord epoch (first seconds of 2015) InternalworkerIDInternalprocessID000000000111Incremented for every generated ID on that process642212017

### Snowflake IDs in Pagination[](https://discord.com/developers/docs/reference#snowflake-ids-in-pagination) 

We typically use snowflake IDs in many of our API routes for pagination. The standardized pagination paradigm we utilize is one in which you can specify IDs `before` and `after` in combination with `limit` to retrieve a desired page of results. You will want to refer to the specific endpoint documentation for details.

It is useful to note that snowflake IDs are just numbers with a timestamp , so when dealing with pagination where you want results from the beginning of time (in Discord Epoch , but `0` works here too) or before/after a specific time you can generate a snowflake ID for that time.

###### Generating a snowflake ID from a Timestamp Example[](https://discord.com/developers/docs/reference#snowflake-ids-in-pagination-generating-a-snowflake-id-from-a-timestamp-example) 

```
(timestamp_ms - DISCORD_EPOCH) << 22
```

## ID Serialization[](https://discord.com/developers/docs/reference#id-serialization) 

There are some cases in which our API and Gateway may return IDs in an unexpected format. Internally , Discord stores IDs as integer snowflakes. When we serialize IDs to JSON , we transform `bigints` into strings. Given that all Discord IDs are snowflakes , you should always expect a string.

However , there are cases in which passing something to our API will instead return IDs serialized as an integer ; this is the case when you send our API or Gateway a value in an `id` field that is not `bigint` size. For example , when requesting `GUILD_MEMBERS_CHUNK` from our gateway:

```
// Send
{
op: 8 , 
d: {
 guild_id: '308994132968210433' , 
 user_ids: [ '123123' ]
}
}

// Receive
{
t: 'GUILD_MEMBERS_CHUNK' , 
s: 3 , 
op: 0 , 
d: {
 not_found: [ 123123 ] , 
 members: [] , 
 guild_id: '308994132968210433'
}
}
```

You can see in this case that the sent `user_id` is not a `bigint` ; therefore , when it is serialized back to JSON by Discord , it is not transformed into a string. This will never happen with IDs that come from Discord. But , this can happen if you send malformed data in your requests.

## ISO8601 Date/Time[](https://discord.com/developers/docs/reference#iso8601-datetime) 

Discord utilizes the [ISO8601 format](https://www.loc.gov/standards/datetime/iso-tc154-wg5_n0038_iso_wd_8601-1_2016-02-16.pdf) for most Date/Times returned in our models. This format is referred to as type `ISO8601` within tables in this documentation.

## Nullable and Optional Resource Fields[](https://discord.com/developers/docs/reference#nullable-and-optional-resource-fields) 

Resource fields that may contain a `null` value have types that are prefixed with a question mark. Resource fields that are optional have names that are suffixed with a question mark.

###### Example Nullable and Optional Fields[](https://discord.com/developers/docs/reference#nullable-and-optional-resource-fields-example-nullable-and-optional-fields) 

<table><thead><tr><th>Field</th><th>Type</th></tr></thead><tbody><tr><td>optional_field ? 

</td><td>string</td></tr><tr><td>nullable_field</td><td>?string</td></tr><tr><td>optional_and_nullable_field ? 

</td><td>?string</td></tr></tbody></table>

## Consistency[](https://discord.com/developers/docs/reference#consistency) 

Discord operates at a scale where true consistency is impossible. Because of this , lots of operations in our API and in-between our services are [eventually consistent](https://en.wikipedia.org/wiki/Eventual_consistency) 

Due to this , client actions can never be serialized and may be executed in any order (if executed at all) 

Along with these constraints , events in Discord may:

* Never be sent to a client
* Be sent exactly one time to the client
* Be sent up to N times per client

Clients should operate on events and results from the API in as much of an idempotent behavior as possible.

## HTTP API[](https://discord.com/developers/docs/reference#http-api) 

### User Agent[](https://discord.com/developers/docs/reference#user-agent) 

Clients using the HTTP API must provide a valid [User Agent](https://www.rfc-editor.org/rfc/rfc9110.html#section-10.1.5) which specifies information about the client library and version in the following format:

###### User Agent Example[](https://discord.com/developers/docs/reference#user-agent-user-agent-example) 

```
User-Agent: DiscordBot ($url , $versionNumber) 
```

Clients may append more information and metadata to the end of this string as they wish.

Client requests that do not have a valid User Agent specified may be blocked and return a [Cloudflare error](https://support.cloudflare.com/hc/en-us/articles/360029779472-Troubleshooting-Cloudflare-1XXX-errors) 

### Content Type[](https://discord.com/developers/docs/reference#content-type) 

Clients using the HTTP API must provide a valid `Content-Type` header , either `application/json` , `application/x-www-form-urlencoded` , or `multipart/form-data` , except where specified. Failing to do so will result in a `50035` "Invalid form body" error.

### Rate Limiting[](https://discord.com/developers/docs/reference#rate-limiting) 

The HTTP API implements a process for limiting and preventing excessive requests in accordance with [RFC 6585](https://tools.ietf.org/html/rfc6585#section-4) 

API users that regularly hit and ignore rate limits will have their API keys revoked , and be blocked from the platform. For more information on rate limiting of requests , please see the [Rate Limits](https://discord.com/developers/docs/topics/rate-limits#rate-limits) section.

### Boolean Query Strings[](https://discord.com/developers/docs/reference#boolean-query-strings) 

Certain endpoints in the API are documented to accept booleans for their query string parameters. While there is no standard system for boolean representation in query string parameters , Discord represents such cases using `True` , `true` , or `1` for true and `False` , `false` or `0` for false.

## Gateway (WebSocket) API[](https://discord.com/developers/docs/reference#gateway-websocket-api) 

Discord's Gateway API is used for maintaining persistent , stateful websocket connections between your client and our servers. These connections are used for sending and receiving real-time events your client can use to track and update local state. The Gateway API uses secure websocket connections as specified in [RFC 6455](https://tools.ietf.org/html/rfc6455) 

For information on opening Gateway connections , please see the [Gateway API](https://discord.com/developers/docs/events/gateway#connections) section.

## Message Formatting[](https://discord.com/developers/docs/reference#message-formatting) 

Discord utilizes a subset of markdown for rendering message content on its clients , while also adding some custom functionality to enable things like mentioning users and channels. This functionality uses the following formats:

###### Formats[](https://discord.com/developers/docs/reference#message-formatting-formats) 

<table><thead><tr><th>Type</th><th>Structure</th><th>Example</th></tr></thead><tbody><tr><td>User</td><td><code>&lt ; @USER_ID&gt ; </code></td><td><code>&lt ; @80351110224678912&gt ; </code></td></tr><tr><td>User *</td><td><code>&lt ; @ ! USER_ID&gt ; </code></td><td><code>&lt ; @ ! 80351110224678912&gt ; </code></td></tr><tr><td>Channel</td><td><code>&lt ; #CHANNEL_ID&gt ; </code></td><td><code>&lt ; #103735883630395392&gt ; </code></td></tr><tr><td>Role</td><td><code>&lt ; @&amp ; ROLE_ID&gt ; </code></td><td><code>&lt ; @&amp ; 165511591545143296&gt ; </code></td></tr><tr><td>Slash Command **</td><td><code>&lt ; /NAME:COMMAND_ID&gt ; </code></td><td><code>&lt ; /airhorn:816437322781949972&gt ; </code></td></tr><tr><td>Standard Emoji</td><td>Unicode Characters</td><td>🦶</td></tr><tr><td>Custom Emoji</td><td><code>&lt ; :NAME:ID&gt ; </code></td><td><code>&lt ; :mmLol:216154654256398347&gt ; </code></td></tr><tr><td>Custom Emoji (Animated) </td><td><code>&lt ; a:NAME:ID&gt ; </code></td><td><code>&lt ; a:b1nzy:392938283556143104&gt ; </code></td></tr><tr><td>Unix Timestamp ***</td><td><code>&lt ; t:TIMESTAMP&gt ; </code></td><td><code>&lt ; t:1618953630&gt ; </code></td></tr><tr><td>Unix Timestamp (Styled) ***</td><td><code>&lt ; t:TIMESTAMP:STYLE&gt ; </code></td><td><code>&lt ; t:1618953630:d&gt ; </code></td></tr><tr><td>Guild Navigation</td><td><code>&lt ; id:TYPE&gt ; </code></td><td><code>&lt ; id:customize&gt ; </code></td></tr><tr><td>Email ****</td><td><code>&lt ; USERNAME@DOMAIN&gt ; </code></td><td><code>&lt ; nelly@discord.com&gt ; </code></td></tr><tr><td>Phone Number ****</td><td><code>&lt ; +PHONE_NUMBER&gt ; </code></td><td><code>&lt ; +1 (555) 123 4567&gt ; </code></td></tr></tbody></table>

Using the markdown for either users , roles , or channels will usually mention the target (s) accordingly , but this can be suppressed using the [`allowed_mentions`](https://discord.com/developers/docs/resources/message#message-object) parameter (when creating a message) 

Standard emoji are currently rendered using [Twemoji](https://github.com/jdecked/twemoji) for Desktop/Android and Apple's native emoji on iOS.

* User mentions with an exclamation mark are deprecated and should be handled like any other user mention.

** Subcommands and subcommand groups can also be mentioned by using respectively `</NAME SUBCOMMAND:ID>` and `</NAME SUBCOMMAND_GROUP SUBCOMMAND:ID>`

*** Timestamps are expressed in seconds and display the given timestamp in the user's timezone and locale.

**** Email and phone number markdown uses `mailto:` and `tel:` URI schemes respectively that can optionally be prefixed (e.g. `<mailto:nelly@discord.com>`) 

Email markdown supports headers , values must be [URL Encoded](https://en.wikipedia.org/wiki/Percent-encoding) (e.g. `<nelly@discord.com?subject=Message%20Title&body=Message%20Content>`) 

###### Timestamp Styles[](https://discord.com/developers/docs/reference#message-formatting-timestamp-styles) 

<table><thead><tr><th>Style</th><th>Example Output</th><th>Description</th></tr></thead><tbody><tr><td>t</td><td>16:20</td><td>Short Time</td></tr><tr><td>T</td><td>16:20:30</td><td>Long Time</td></tr><tr><td>d</td><td>20/04/2021</td><td>Short Date</td></tr><tr><td>D</td><td>20 April 2021</td><td>Long Date</td></tr><tr><td>f *</td><td>20 April 2021 16:20</td><td>Short Date/Time</td></tr><tr><td>F</td><td>Tuesday , 20 April 2021 16:20</td><td>Long Date/Time</td></tr><tr><td>R</td><td>2 months ago</td><td>Relative Time</td></tr></tbody></table>

* Default style used when no style is specified.

###### Guild Navigation Types[](https://discord.com/developers/docs/reference#message-formatting-guild-navigation-types) 

Guild navigation types link to the corresponding resource in the current server.

<table><thead><tr><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>customize</td><td><span class="italics-1aHcnm">Customize</span> tab with the server's <a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-onboarding-object" data-discover="true">onboarding prompts</a></td></tr><tr><td>browse</td><td><span class="italics-1aHcnm">Browse Channels</span> tab</td></tr><tr><td>guide</td><td><a class="anchor-1MIwyf link-3m0lUT" href="https://support.discord.com/hc/en-us/articles/13497665141655" rel="noreferrer noopener" target="_blank" role="button" tabindex="0">Server Guide</a></td></tr><tr><td>linked-roles</td><td><a class="anchor-1MIwyf link-3m0lUT" href="https://support.discord.com/hc/en-us/articles/10388356626711" rel="noreferrer noopener" target="_blank" role="button" tabindex="0">Linked Roles</a></td></tr><tr><td>linked-roles<div></div></td><td><span class="italics-1aHcnm">Linked Role</span> connection</td></tr></tbody></table>

## Image Formatting[](https://discord.com/developers/docs/reference#image-formatting) 

###### Image Base Url[](https://discord.com/developers/docs/reference#image-formatting-image-base-url) 

```
https://cdn.discordapp.com/
```

Discord uses ids and hashes to render images in the client. These hashes can be retrieved through various API requests , like [Get User](https://discord.com/developers/docs/resources/user#get-user) 

Below are the formats , size limitations , and CDN endpoints for images in Discord. The returned format can be changed by changing the [extension name](https://discord.com/developers/docs/reference#image-formatting-image-formats) at the end of the URL. The returned size can be changed by appending a querystring of `?size=desired_size` to the URL. Image size can be any power of two between 16 and 4096.

###### Image Formats[](https://discord.com/developers/docs/reference#image-formatting-image-formats) 

<table><thead><tr><th>Name</th><th>Extension</th></tr></thead><tbody><tr><td>JPEG</td><td>.jpg , .jpeg</td></tr><tr><td>PNG</td><td>.png</td></tr><tr><td>WebP</td><td>.webp</td></tr><tr><td>GIF</td><td>.gif</td></tr><tr><td>AVIF</td><td>.avif</td></tr><tr><td>Lottie</td><td>.json</td></tr></tbody></table>

###### CDN Endpoints[](https://discord.com/developers/docs/reference#image-formatting-cdn-endpoints) 

<table><thead><tr><th>Type</th><th>Path</th><th>Supports</th></tr></thead><tbody><tr><td>Custom Emoji</td><td>emojis/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/emoji#emoji-object" data-discover="true">emoji_id</a>.png *****</td><td>PNG , JPEG , WebP , GIF , AVIF</td></tr><tr><td>Guild Icon</td><td>icons/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_icon</a>.png *</td><td>PNG , JPEG , WebP , GIF</td></tr><tr><td>Guild Splash</td><td>splashes/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_splash</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Guild Discovery Splash</td><td>discovery-splashes/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_discovery_splash</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Guild Banner</td><td>banners/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_banner</a>.png *</td><td>PNG , JPEG , WebP , GIF</td></tr><tr><td>User Banner</td><td>banners/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user_banner</a>.png *</td><td>PNG , JPEG , WebP , GIF</td></tr><tr><td>Default User Avatar</td><td>embed/avatars/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">index</a>.png ** ***</td><td>PNG</td></tr><tr><td>User Avatar</td><td>avatars/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user_avatar</a>.png *</td><td>PNG , JPEG , WebP , GIF</td></tr><tr><td>Guild Member Avatar</td><td>guilds/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/users/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user_id</a>/avatars/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">member_avatar</a>.png *</td><td>PNG , JPEG , WebP , GIF</td></tr><tr><td>Avatar Decoration</td><td>avatar-decoration-presets/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#avatar-decoration-data-object" data-discover="true">avatar_decoration_data_asset</a>.png</td><td>PNG</td></tr><tr><td>Application Icon</td><td>app-icons/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">application_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">icon</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Application Cover</td><td>app-icons/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">application_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">cover_image</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Application Asset</td><td>app-assets/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">application_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/events/gateway-events#activity-object-activity-assets" data-discover="true">asset_id</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Achievement Icon</td><td>app-assets/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">application_id</a>/achievements/<a class="anchor-1MIwyf link-3m0lUT" href="https://github.com/discord/discord-api-docs/blob/legacy-gamesdk/docs/game_sdk/Achievements.md#user-achievement-struct" rel="noreferrer noopener" target="_blank" role="button" tabindex="0">achievement_id</a>/icons/<a class="anchor-1MIwyf link-3m0lUT" href="https://github.com/discord/discord-api-docs/blob/legacy-gamesdk/docs/game_sdk/Achievements.md#user-achievement-struct" rel="noreferrer noopener" target="_blank" role="button" tabindex="0">icon_hash</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Store Page Asset</td><td>app-assets/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/application#application-object" data-discover="true">application_id</a>/store/asset_id</td><td>PNG , JPEG , WebP</td></tr><tr><td>Sticker Pack Banner</td><td>app-assets/710982414301790216/store/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/sticker#sticker-pack-object" data-discover="true">sticker_pack_banner_asset_id</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Team Icon</td><td>team-icons/<a class="link-3m0lUT" href="https://discord.com/developers/docs/topics/teams#data-models-team-object" data-discover="true">team_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/topics/teams#data-models-team-object" data-discover="true">team_icon</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Sticker</td><td>stickers/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/sticker#sticker-object" data-discover="true">sticker_id</a>.png *** ****</td><td>PNG , Lottie , GIF</td></tr><tr><td>Role Icon</td><td>role-icons/<a class="link-3m0lUT" href="https://discord.com/developers/docs/topics/permissions#role-object" data-discover="true">role_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/topics/permissions#role-object" data-discover="true">role_icon</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Guild Scheduled Event Cover</td><td>guild-events/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild-scheduled-event#guild-scheduled-event-object" data-discover="true">scheduled_event_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild-scheduled-event#guild-scheduled-event-object" data-discover="true">scheduled_event_cover_image</a>.png</td><td>PNG , JPEG , WebP</td></tr><tr><td>Guild Member Banner</td><td>guilds/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/users/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user_id</a>/banners/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">member_banner</a>.png *</td><td>PNG , JPEG , WebP , GIF</td></tr><tr><td>Guild Tag Badge</td><td>guild-tag-badges/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">guild_id</a>/<a class="link-3m0lUT" href="https://discord.com/developers/docs/resources/user#user-object-user-primary-guild" data-discover="true">badge_hash</a>.png</td><td>PNG , JPEG , WebP</td></tr></tbody></table>

* In the case of endpoints that support GIFs , the hash will begin with `a_` if it is available in GIF format. These images can also be retrieved as animated WebP using the `?animated=true` querystring parameter. (example: `a_1269e74af4df7417b13759eae50c83dc`) 

** In the case of the Default User Avatar endpoint , the value for `index` depends on whether the user is [migrated to the new username system](https://discord.com/developers/docs/change-log#unique-usernames-on-discord) 

For users on the new username system , `index` will be ` (user_id >> 22) % 6`

For users on the legacy username system , `index` will be `discriminator % 5`

*** In the case of the Default User Avatar and Sticker endpoints , the size of images returned is constant with the "size" querystring parameter being ignored.

**** In the case of the Sticker endpoint , the sticker will be available as PNG if its [`format_type`](https://discord.com/developers/docs/resources/sticker#sticker-object) is `PNG` or `APNG` , GIF if its `format_type` is `GIF` , and as [Lottie](https://airbnb.io/lottie/#/) if its `format_type` is `LOTTIE`

***** For Custom Emoji , we highly recommend requesting emojis as WebP for maximum performance and compatibility. Emojis can be uploaded as JPEG , PNG , GIF , WebP , and AVIF formats. WebP and AVIF formats must be requested as WebP since they don't convert well to other formats. The Discord client uses WebP for all emojis displayed in-app. See the [Emoji Resource](https://discord.com/developers/docs/resources/emoji) page for more details.

Sticker GIFs do not use the CDN base url , and can be accessed at `https://media.discordapp.net/stickers/<sticker_id>.gif`

## Image Data[](https://discord.com/developers/docs/reference#image-data) 

Image data is a [Data URI scheme](https://en.wikipedia.org/wiki/Data_URI_scheme) that supports JPG , GIF , and PNG formats. An example Data URI format is:

```
data:image/jpeg ; base64 , BASE64_ENCODED_JPEG_IMAGE_DATA
```

Ensure you use the proper content type (`image/jpeg` , `image/png` , `image/gif`) that matches the image data being provided.

### Signed Attachment CDN URLs[](https://discord.com/developers/docs/reference#signed-attachment-cdn-urls) 

Attachments uploaded to Discord's CDN (like user and bot-uploaded images) have signed URLs with a preset expiry time. Discord automatically refreshes attachment CDN URLs that appear within the client , so when your app receives a payload with a signed URL (like when you [fetch a message](https://discord.com/developers/docs/resources/message#get-channel-message) ) , it will be valid.

When passing CDN URLs into API fields , like [`url` in an embed image object](https://discord.com/developers/docs/resources/message#embed-object-embed-image-structure) and [`avatar_url` for webhooks](https://discord.com/developers/docs/resources/webhook#execute-webhook-jsonform-params) , your app can pass the CDN URL without any parameters as the value and Discord will automatically render and refresh the URL.

The [standard CDN endpoints](https://discord.com/developers/docs/reference#image-formatting-cdn-endpoints) listed above are not signed , so they will not expire.

###### Example Attachment CDN URL[](https://discord.com/developers/docs/reference#signed-attachment-cdn-urls-example-attachment-cdn-url) 

```
https://cdn.discordapp.com/attachments/1012345678900020080/1234567891233211234/my_image.png?ex=65d903de&is=65c68ede&hm=2481f30dd67f503f54d020ae3b5533b9987fae4e55f2b4e3926e08a3fa3ee24f&
```

###### Attachment CDN URL Parameters[](https://discord.com/developers/docs/reference#signed-attachment-cdn-urls-attachment-cdn-url-parameters) 

<table><thead><tr><th>Parameter</th><th>Description</th></tr></thead><tbody><tr><td>ex</td><td>Hex timestamp indicating when an attachment CDN URL will expire</td></tr><tr><td>is</td><td>Hex timestamp indicating when the URL was issued</td></tr><tr><td>hm</td><td>Unique signature that remains valid until the URL's expiration</td></tr></tbody></table>

## Uploading Files[](https://discord.com/developers/docs/reference#uploading-files) 

The file upload size limit applies to each file in a request. The default limit is `10 MiB` for all users , but may be higher for users depending on their [Nitro](https://support.discord.com/hc/en-us/articles/115000435108-What-are-Nitro-Nitro-Basic) status or by the server's [Boost Tier](https://support.discord.com/hc/en-us/articles/360028038352-Server-Boosting-FAQ-#h_419c3bd5-addd-4989-b7cf-c7957ef92583) 

The `attachment_size_limit` value provided [when working with interactions](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-structure) is calculated as the maximum of these values.

Some endpoints support file attachments , indicated by the `files[n]` parameter. To add file (s) , the standard `application/json` body must be replaced by a `multipart/form-data` body. The JSON message body can optionally be provided using the `payload_json` parameter.

All `files[n]` parameters must include a valid `Content-Disposition` subpart header with a `filename` and unique `name` parameter. Each file parameter must be uniquely named in the format `files[n]` such as `files[0]` , `files[1]` , or `files[42]`

The suffixed index `n` is the snowflake placeholder that can be used in the `attachments` field , which can be passed to the `payload_json` parameter (or [Callback Data Payloads](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-data-structure) ) 

Images can also be referenced in embeds using the `attachment://filename` URL. The `filename` for these URLs must be ASCII alphanumeric with underscores , dashes , or dots. An example payload is provided below.

### Editing Message Attachments[](https://discord.com/developers/docs/reference#editing-message-attachments) 

The `attachments` JSON parameter includes all files that will be appended to the message , including new files and their respective snowflake placeholders (referenced above) 

When making a `PATCH` request , only files listed in the `attachments` parameter will be appended to the message. Any previously-added files that aren't included will be removed.

###### Example Request Bodies (multipart/form-data) [](https://discord.com/developers/docs/reference#editing-message-attachments-example-request-bodies-multipartformdata) 

Note that these examples are small sections of an HTTP request to demonstrate behavior of this endpoint - client libraries will set their own form boundaries (`boundary` is just an example) 

For more information , refer to the [multipart/form-data spec](https://tools.ietf.org/html/rfc7578#section-4) 

This example demonstrates usage of the endpoint without `payload_json`

```
--boundary
Content-Disposition: form-data ; name="content"

Hello , World ! 
--boundary
Content-Disposition: form-data ; name="tts"

true
--boundary--
```

This example demonstrates usage of the endpoint with `payload_json` and all content fields (`content` , `embeds` , `files[n]`) set.

```
--boundary
Content-Disposition: form-data ; name="payload_json"
Content-Type: application/json

{
"content": "Hello , World ! " , 
"embeds": [{
 "title": "Hello , Embed ! " , 
 "description": "This is an embedded message" 

, 
 "thumbnail": {
  "url": "attachment://myfilename.png"
 } , 
 "image": {
  "url": "attachment://mygif.gif"
 }
}] , 
"message_reference": {
 "message_id": "233648473390448641"
} , 
"attachments": [{
  "id": 0 , 
  "description": "Image of a cute little cat" , 
  "filename": "myfilename.png"
} , {
  "id": 1 , 
  "description": "Rickroll gif" , 
  "filename": "mygif.gif"
}]
}
--boundary
Content-Disposition: form-data ; name="files[0]" ; filename="myfilename.png"
Content-Type: image/png

[image bytes]
--boundary
Content-Disposition: form-data ; name="files[1]" ; filename="mygif.gif"
Content-Type: image/gif

[image bytes]
--boundary--
```

###### Using Attachments within Embeds[](https://discord.com/developers/docs/reference#editing-message-attachments-using-attachments-within-embeds) 

You can upload attachments when creating a message and use those attachments within your embed. To do this , you will want to upload files as part of your `multipart/form-data` body. Make sure that you're uploading files which contain a filename , as you will need to reference it in your payload.

Only `.jpg` , `.jpeg` , `.png` , `.webp` , and `.gif` may be used at this time. Other file types are not supported.

Within an embed object , you can set an image to use an attachment as its URL with the attachment scheme syntax: `attachment://filename.png`

For example:

```
{
"embeds": [{
 "image": {
  "url": "attachment://screenshot.png"
 }
}]
}
```

## Locales[](https://discord.com/developers/docs/reference#locales) 

<table><thead><tr><th>Locale</th><th>Language Name</th><th>Native Name</th></tr></thead><tbody><tr><td>id</td><td>Indonesian</td><td>Bahasa Indonesia</td></tr><tr><td>da</td><td>Danish</td><td>Dansk</td></tr><tr><td>de</td><td>German</td><td>Deutsch</td></tr><tr><td>en-GB</td><td>English , UK</td><td>English , UK</td></tr><tr><td>en-US</td><td>English , US</td><td>English , US</td></tr><tr><td>es-ES</td><td>Spanish</td><td>Español</td></tr><tr><td>es-419</td><td>Spanish , LATAM</td><td>Español , LATAM</td></tr><tr><td>fr</td><td>French</td><td>Français</td></tr><tr><td>hr</td><td>Croatian</td><td>Hrvatski</td></tr><tr><td>it</td><td>Italian</td><td>Italiano</td></tr><tr><td>lt</td><td>Lithuanian</td><td>Lietuviškai</td></tr><tr><td>hu</td><td>Hungarian</td><td>Magyar</td></tr><tr><td>nl</td><td>Dutch</td><td>Nederlands</td></tr><tr><td>no</td><td>Norwegian</td><td>Norsk</td></tr><tr><td>pl</td><td>Polish</td><td>Polski</td></tr><tr><td>pt-BR</td><td>Portuguese , Brazilian</td><td>Português do Brasil</td></tr><tr><td>ro</td><td>Romanian , Romania</td><td>Română</td></tr><tr><td>fi</td><td>Finnish</td><td>Suomi</td></tr><tr><td>sv-SE</td><td>Swedish</td><td>Svenska</td></tr><tr><td>vi</td><td>Vietnamese</td><td>Tiếng Việt</td></tr><tr><td>tr</td><td>Turkish</td><td>Türkçe</td></tr><tr><td>cs</td><td>Czech</td><td>Čeština</td></tr><tr><td>el</td><td>Greek</td><td>Ελληνικά</td></tr><tr><td>bg</td><td>Bulgarian</td><td>български</td></tr><tr><td>ru</td><td>Russian</td><td>Pусский</td></tr><tr><td>uk</td><td>Ukrainian</td><td>Українська</td></tr><tr><td>hi</td><td>Hindi</td><td>हिन्दी</td></tr><tr><td>th</td><td>Thai</td><td>ไทย</td></tr><tr><td>zh-CN</td><td>Chinese , China</td><td>中文</td></tr><tr><td>ja</td><td>Japanese</td><td>日本語</td></tr><tr><td>zh-TW</td><td>Chinese , Taiwan</td><td>繁體中文</td></tr><tr><td>ko</td><td>Korean</td><td>한국어</td></tr></tbody></table>