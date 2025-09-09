---
url: https://discord.com/developers/docs/interactions/receiving-and-responding
time: 2025-09-10P22:49:19
tags: 
---
An [Interaction](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object) is the message that your application receives when a user uses an application command or a message component.

For [Slash Commands](https://discord.com/developers/docs/interactions/application-commands#slash-commands), it includes the values that the user submitted.

For [User Commands](https://discord.com/developers/docs/interactions/application-commands#user-commands) and [Message Commands](https://discord.com/developers/docs/interactions/application-commands#message-commands), it includes the resolved user or message on which the action was taken.

For [Message Components](https://discord.com/developers/docs/components/reference) it includes identifying information about the component that was used. It will also include some metadata about how the interaction was triggered: the `guild_id`, `channel`, `member` and other fields. You can find all the values in our data models below.

### Interaction Object[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object)

###### Interaction Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-structure)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>snowflake</td><td>ID of the interaction</td></tr><tr><td>application_id</td><td>snowflake</td><td>ID of the application this interaction is for</td></tr><tr><td>type</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type" data-discover="true">interaction type</a></td><td>Type of interaction</td></tr><tr><td>data?*</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-data" data-discover="true">interaction data</a></td><td>Interaction data payload</td></tr><tr><td>guild?</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">partial guild</a> object</td><td>Guild that the interaction was sent from</td></tr><tr><td>guild_id?</td><td>snowflake</td><td>Guild that the interaction was sent from</td></tr><tr><td>channel?</td><td><a href="https://discord.com/developers/docs/resources/channel#channel-object" data-discover="true">partial channel</a> object</td><td>Channel that the interaction was sent from</td></tr><tr><td>channel_id?</td><td>snowflake</td><td>Channel that the interaction was sent from</td></tr><tr><td>member?**</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">guild member</a> object</td><td>Guild member data for the invoking user, including permissions</td></tr><tr><td>user?</td><td><a href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user</a> object</td><td>User object for the invoking user, if invoked in a DM</td></tr><tr><td>token</td><td>string</td><td>Continuation token for responding to the interaction</td></tr><tr><td>version</td><td>integer</td><td>Read-only property, always <code>1</code></td></tr><tr><td>message?</td><td><a href="https://discord.com/developers/docs/resources/message#message-object" data-discover="true">message</a> object</td><td>For components or modals triggered by components, the message they were attached to</td></tr><tr><td>app_permissions***</td><td>string</td><td>Bitwise set of permissions the app has in the source location of the interaction</td></tr><tr><td>locale?****</td><td>string</td><td>Selected <a href="https://discord.com/developers/docs/reference#locales" data-discover="true">language</a> of the invoking user</td></tr><tr><td>guild_locale?</td><td>string</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">Guild's preferred locale</a>, if invoked in a guild</td></tr><tr><td>entitlements</td><td>array of <a href="https://discord.com/developers/docs/resources/entitlement#entitlement-object" data-discover="true">entitlement</a> objects</td><td>For <a href="https://discord.com/developers/docs/monetization/overview" data-discover="true">monetized apps</a>, any entitlements for the invoking user, representing access to premium <a href="https://discord.com/developers/docs/resources/sku" data-discover="true">SKUs</a></td></tr><tr><td>authorizing_integration_owners</td><td>dictionary with keys of <a href="https://discord.com/developers/docs/resources/application#application-object-application-integration-types" data-discover="true">application integration types</a></td><td>Mapping of installation contexts that the interaction was authorized for to related user or guild IDs. See <a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-authorizing-integration-owners-object" data-discover="true">Authorizing Integration Owners Object</a> for details</td></tr><tr><td>context?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-context-types" data-discover="true">interaction context type</a></td><td>Context where the interaction was triggered from</td></tr><tr><td>attachment_size_limit</td><td>integer</td><td>Attachment size limit in bytes</td></tr></tbody></table>

* This is always present on application command, message component, and modal submit interaction types. It is optional for future-proofing against new interaction types

** `member` is sent when the interaction is invoked in a guild, and `user` is sent when invoked in a DM

*** `app_permissions` includes `ATTACH_FILES | EMBED_LINKS | MENTION_EVERYONE` permissions for (G)DMs with other users, and additionally includes `USE_EXTERNAL_EMOJIS` for DMs with the app's bot user

**** This is available on all interaction types except PING

###### Interaction Type[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type)

<table><thead><tr><th>Name</th><th>Value</th></tr></thead><tbody><tr><td>PING</td><td>1</td></tr><tr><td>APPLICATION_COMMAND</td><td>2</td></tr><tr><td>MESSAGE_COMPONENT</td><td>3</td></tr><tr><td>APPLICATION_COMMAND_AUTOCOMPLETE</td><td>4</td></tr><tr><td>MODAL_SUBMIT</td><td>5</td></tr></tbody></table>

###### Interaction Context Types[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-context-types)

Context in Discord where an interaction can be used, or where it was triggered from. Details about using interaction contexts for application commands is in the [commands context documentation](https://discord.com/developers/docs/interactions/application-commands#interaction-contexts).

<table><thead><tr><th>Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>GUILD</td><td>0</td><td>Interaction can be used within servers</td></tr><tr><td>BOT_DM</td><td>1</td><td>Interaction can be used within DMs with the app's bot user</td></tr><tr><td>PRIVATE_CHANNEL</td><td>2</td><td>Interaction can be used within Group DMs and DMs other than the app's bot user</td></tr></tbody></table>

The `authorizing_integration_owners` field includes details about the authorizing user or server for the installation(s) relevant to the interaction. For apps installed to a user, it can be used to tell the difference between the authorizing user and the user that triggered an interaction (like a message component).

A key will only be present if the following are true:

*   The app has been authorized to the [installation context](https://discord.com/developers/docs/resources/application#application-object-application-integration-types) corresponding to the key (`GUILD_INSTALL` or `USER_INSTALL`)
*   The interaction is supported in the source [interaction context](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-context-types) (`GUILD`, `BOT_DM`, or `PRIVATE_CHANNEL`) for the installation context corresponding to the key
*   And for command invocations, the command must be supported in the installation context (using [`integration_types`](https://discord.com/developers/docs/interactions/application-commands#contexts))

The values in `authorizing_integration_owners` depend on the key—

*   If the key is `GUILD_INSTALL` (`"0"`), the value depends on the source of the interaction:
    *   The value will be the guild ID if the interaction is triggered from a server
    *   The value will be `"0"` if the interaction is triggered from a DM with the app's bot user
*   If the key is `USER_INSTALL` (`"1"`), the value will be the ID of the authorizing user

###### Interaction Data[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-data)

While the `data` field is guaranteed to be present for all [interaction types](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type) besides `PING`, its structure will vary. The following tables detail the inner `data` payload for each interaction type.

<table><thead><tr><th>Interaction Type</th><th>Interaction Data</th></tr></thead><tbody><tr><td>PING (<code>1</code>)</td><td>N / A</td></tr><tr><td>APPLICATION_COMMAND (<code>2</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-data-structure" data-discover="true">Application Command Data Structure</a></td></tr><tr><td>MESSAGE_COMPONENT (<code>3</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-message-component-data-structure" data-discover="true">Message Component Data Structure</a></td></tr><tr><td>APPLICATION_COMMAND_AUTOCOMPLETE (<code>4</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-data-structure" data-discover="true">Application Command Data Structure</a></td></tr><tr><td>MODAL_SUBMIT (<code>5</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-modal-submit-data-structure" data-discover="true">Modal Submit Data Structure</a></td></tr></tbody></table>

###### Application Command Data Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-data-structure)

Sent in `APPLICATION_COMMAND` and `APPLICATION_COMMAND_AUTOCOMPLETE` interactions.

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>snowflake</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true"><code>ID</code></a> of the invoked command</td></tr><tr><td>name</td><td>string</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true"><code>name</code></a> of the invoked command</td></tr><tr><td>type</td><td>integer</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true"><code>type</code></a> of the invoked command</td></tr><tr><td>resolved?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-resolved-data-structure" data-discover="true">resolved data</a></td><td>Converted users + roles + channels + attachments</td></tr><tr><td>options?*</td><td>array of <a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-interaction-data-option-structure" data-discover="true">application command interaction data option</a></td><td>Params + values from the user</td></tr><tr><td>guild_id?</td><td>snowflake</td><td>ID of the guild the command is registered to</td></tr><tr><td>target_id?</td><td>snowflake</td><td>ID of the user or message targeted by a <a href="https://discord.com/developers/docs/interactions/application-commands#user-commands" data-discover="true">user</a> or <a href="https://discord.com/developers/docs/interactions/application-commands#message-commands" data-discover="true">message</a> command</td></tr></tbody></table>

* This [can be partial](https://discord.com/developers/docs/interactions/application-commands#autocomplete) when in response to `APPLICATION_COMMAND_AUTOCOMPLETE`

###### Message Component Data Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-message-component-data-structure)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>custom_id</td><td>string</td><td><a href="https://discord.com/developers/docs/components/reference#anatomy-of-a-component-custom-id" data-discover="true"><code>custom_id</code></a> of the component</td></tr><tr><td>component_type</td><td>integer</td><td><a href="https://discord.com/developers/docs/components/reference#component-object-component-types" data-discover="true">type</a> of the component</td></tr><tr><td>values?*</td><td>array of <a href="https://discord.com/developers/docs/components/reference#string-select-select-option-structure" data-discover="true">select option values</a></td><td>Values the user selected in a <a href="https://discord.com/developers/docs/components/reference#string-select" data-discover="true">select menu</a> component</td></tr><tr><td>resolved?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-resolved-data-structure" data-discover="true">resolved data</a></td><td>Resolved entities from selected options</td></tr></tbody></table>

* This is always present for select menu components

###### Modal Submit Data Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-modal-submit-data-structure)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>custom_id</td><td>string</td><td>The custom ID provided for the modal</td></tr><tr><td>components</td><td>array of <a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-component-interaction-response-structures" data-discover="true">component interaction response</a></td><td>Values submitted by the user</td></tr></tbody></table>

###### Component Interaction Response Structures[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-component-interaction-response-structures)

<table><thead><tr><th>Component</th></tr></thead><tbody><tr><td><a href="https://discord.com/developers/docs/components/reference#string-select-string-select-interaction-response-structure" data-discover="true">String Select</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#text-input-text-input-interaction-response-structure" data-discover="true">Text Input</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#user-select-user-select-interaction-response-structure" data-discover="true">User Select</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#role-select-role-select-interaction-response-structure" data-discover="true">Role Select</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#mentionable-select-mentionable-select-interaction-response-structure" data-discover="true">Mentionable Select</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#channel-select-channel-select-interaction-response-structure" data-discover="true">Channel Select</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#text-display-text-display-interaction-response-structure" data-discover="true">Text Display</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#label-label-interaction-response-structure" data-discover="true">Label</a></td></tr></tbody></table>

###### Resolved Data Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-resolved-data-structure)

If data for a Member is included, data for its corresponding User will also be included.

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>users?</td><td>Map of Snowflakes to <a href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user</a> objects</td><td>IDs and User objects</td></tr><tr><td>members?*</td><td>Map of Snowflakes to <a href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">partial member</a> objects</td><td>IDs and partial Member objects</td></tr><tr><td>roles?</td><td>Map of Snowflakes to <a href="https://discord.com/developers/docs/topics/permissions#role-object" data-discover="true">role</a> objects</td><td>IDs and Role objects</td></tr><tr><td>channels?**</td><td>Map of Snowflakes to <a href="https://discord.com/developers/docs/resources/channel#channel-object" data-discover="true">partial channel</a> objects</td><td>IDs and partial Channel objects</td></tr><tr><td>messages?</td><td>Map of Snowflakes to <a href="https://discord.com/developers/docs/resources/message#message-object" data-discover="true">partial messages</a> objects</td><td>IDs and partial Message objects</td></tr><tr><td>attachments?</td><td>Map of Snowflakes to <a href="https://discord.com/developers/docs/resources/message#attachment-object" data-discover="true">attachment</a> objects</td><td>IDs and attachment objects</td></tr></tbody></table>

* Partial `Member` objects are missing `user`, `deaf` and `mute` fields

** Partial `Channel` objects only have `id`, `name`, `type` and `permissions` fields. Threads will also have `thread_metadata` and `parent_id` fields.

###### Application Command Interaction Data Option Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-interaction-data-option-structure)

All options have names, and an option can either be a parameter and input value--in which case `value` will be set--or it can denote a subcommand or group--in which case it will contain a top-level key and another array of `options`.

`value` and `options` are mutually exclusive.

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>Name of the parameter</td></tr><tr><td>type</td><td>integer</td><td>Value of <a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-type" data-discover="true">application command option type</a></td></tr><tr><td>value?</td><td>string, integer, double, or boolean</td><td>Value of the option resulting from user input</td></tr><tr><td>options?</td><td>array of <a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-interaction-data-option-structure" data-discover="true">application command interaction data option</a></td><td>Present if this option is a group or subcommand</td></tr><tr><td>focused?</td><td>boolean</td><td><code>true</code> if this option is the currently focused option for autocomplete</td></tr></tbody></table>

### Message Interaction Object[](https://discord.com/developers/docs/interactions/receiving-and-responding#message-interaction-object)

This is sent on the [message object](https://discord.com/developers/docs/resources/message#message-object) when the message is a response to an Interaction without an existing message.

###### Message Interaction Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#message-interaction-object-message-interaction-structure)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>snowflake</td><td>ID of the interaction</td></tr><tr><td>type</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type" data-discover="true">interaction type</a></td><td>Type of interaction</td></tr><tr><td>name</td><td>string</td><td>Name of the <a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true">application command</a>, including subcommands and subcommand groups</td></tr><tr><td>user</td><td><a href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">user object</a></td><td>User who invoked the interaction</td></tr><tr><td>member?</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">partial member</a> object</td><td>Member who invoked the interaction in the guild</td></tr></tbody></table>

## Receiving an Interaction[](https://discord.com/developers/docs/interactions/receiving-and-responding#receiving-an-interaction)

When a user interacts with your app, your app will receive an [Interaction](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object). Your app can receive an interaction in one of two ways:

*   Via [Interaction Create](https://discord.com/developers/docs/events/gateway-events#interaction-create) gateway event
*   Via outgoing webhook

These two methods are mutually exclusive; you can only receive Interactions one of the two ways. The `INTERACTION_CREATE` [Gateway Event](https://discord.com/developers/docs/events/gateway-events#interaction-create) may be handled by connected clients, while the webhook method detailed below does not require a connected client.

If you want to receive interactions via HTTP-based outgoing webhooks, you must configure an Interactions Endpoint URL for your app. You can read about preparing and adding an Interactions Endpoint URL to your app in the [Preparing for Interactions](https://discord.com/developers/docs/interactions/overview#preparing-for-interactions) section in Interactions Overview.

### Interaction Metadata[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-metadata)

An [Interaction](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object) includes metadata to aid your application in handling it as well as `data` specific to the interaction type. You can find samples for each interaction type on their respective pages:

*   [Slash Commands](https://discord.com/developers/docs/interactions/application-commands#slash-commands-example-interaction)
*   [User Commands](https://discord.com/developers/docs/interactions/application-commands#user-commands-example-interaction)
*   [Message Commands](https://discord.com/developers/docs/interactions/application-commands#message-commands-example-interaction)
*   [Message Components](https://discord.com/developers/docs/components/using-message-components)
*   [Modal Components](https://discord.com/developers/docs/components/using-modal-components)

An explanation of all the fields can be found in our [data models](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object).

Now that you've gotten the data from the user, it's time to respond to them.

## Responding to an Interaction[](https://discord.com/developers/docs/interactions/receiving-and-responding#responding-to-an-interaction)

Interactions--both receiving and responding--are webhooks under the hood. So responding to an Interaction is just like sending a webhook request!

Interaction responses have the same header requirements as normal HTTP API requests. See [here](https://discord.com/developers/docs/reference#http-api) for further information.

There are a number of ways you can respond to an interaction:

### Interaction Response Object[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object)

###### Interaction Response Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-response-structure)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type" data-discover="true">interaction callback type</a></td><td>Type of response</td></tr><tr><td>data?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-data-structure" data-discover="true">interaction callback data</a></td><td>An optional response message</td></tr></tbody></table>

###### Interaction Callback Type[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type)

<table><thead><tr><th>Name</th><th>Value</th><th>Description</th></tr></thead><tbody><tr><td>PONG</td><td>1</td><td>ACK a <code>Ping</code></td></tr><tr><td>CHANNEL_MESSAGE_WITH_SOURCE</td><td>4</td><td>Respond to an interaction with a message</td></tr><tr><td>DEFERRED_CHANNEL_MESSAGE_WITH_SOURCE</td><td>5</td><td>ACK an interaction and edit a response later, the user sees a loading state</td></tr><tr><td>DEFERRED_UPDATE_MESSAGE*</td><td>6</td><td>For components, ACK an interaction and edit the original message later; the user does not see a loading state</td></tr><tr><td>UPDATE_MESSAGE*</td><td>7</td><td>For components, edit the message the component was attached to</td></tr><tr><td>APPLICATION_COMMAND_AUTOCOMPLETE_RESULT</td><td>8</td><td>Respond to an autocomplete interaction with suggested choices</td></tr><tr><td>MODAL**</td><td>9</td><td>Respond to an interaction with a popup modal</td></tr><tr><td>PREMIUM_REQUIRED</td><td>10</td><td><a href="https://discord.com/developers/docs/change-log#premium-apps-new-premium-button-style-deep-linking-url-schemes" data-discover="true"><span>Deprecated</span></a>; respond to an interaction with an upgrade button, only available for apps with <a href="https://discord.com/developers/docs/monetization/overview" data-discover="true">monetization</a> enabled</td></tr><tr><td>LAUNCH_ACTIVITY</td><td>12</td><td>Launch the Activity associated with the app. Only available for apps with <a href="https://discord.com/developers/docs/activities/overview" data-discover="true">Activities</a> enabled</td></tr></tbody></table>

* Only valid for [component-based](https://discord.com/developers/docs/components/reference) interactions

** Not available for `MODAL_SUBMIT` and `PING` interactions.

###### Interaction Callback Data Structure[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-data-structure)

###### Messages[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-messages)

Not all message fields are currently supported.

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>tts?</td><td>boolean</td><td>Whether the response is TTS</td></tr><tr><td>content?</td><td>string</td><td>Message content</td></tr><tr><td>embeds?</td><td>array of <a href="https://discord.com/developers/docs/resources/message#embed-object" data-discover="true">embeds</a></td><td>Supports up to 10 embeds</td></tr><tr><td>allowed_mentions?</td><td><a href="https://discord.com/developers/docs/resources/message#allowed-mentions-object" data-discover="true">allowed mentions</a></td><td><a href="https://discord.com/developers/docs/resources/message#allowed-mentions-object" data-discover="true">Allowed mentions</a> object</td></tr><tr><td>flags? *</td><td>integer</td><td><a href="https://discord.com/developers/docs/resources/message#message-object-message-flags" data-discover="true">Message flags</a> combined as a <a href="https://en.wikipedia.org/wiki/Bit_field" rel="noreferrer noopener" target="_blank" role="button" tabindex="0">bitfield</a> (only <code>SUPPRESS_EMBEDS</code>, <code>EPHEMERAL</code>, <code>IS_COMPONENTS_V2</code>, <code>IS_VOICE_MESSAGE</code>, and <code>SUPPRESS_NOTIFICATIONS</code> can be set)</td></tr><tr><td>components?</td><td>array of <a href="https://discord.com/developers/docs/components/reference#component-object" data-discover="true">components</a></td><td>Message components</td></tr><tr><td>attachments? **</td><td>array of partial <a href="https://discord.com/developers/docs/resources/message#attachment-object" data-discover="true">attachment</a> objects</td><td>Attachment objects with filename and description</td></tr><tr><td>poll?</td><td><a href="https://discord.com/developers/docs/resources/poll#poll-create-request-object" data-discover="true">poll</a> request object</td><td>Details about the poll</td></tr></tbody></table>

* If you create a callback with the [type](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type) `DEFERRED_CHANNEL_MESSAGE_WITH_SOURCE` the only valid [message flag](https://discord.com/developers/docs/resources/message#message-object-message-flags) you may use is `EPHEMERAL`. If you'd like to create a component based message with `IS_COMPONENTS_V2` you must do that with the [followup](https://discord.com/developers/docs/interactions/receiving-and-responding#followup-messages) message, not this one.

** See [Uploading Files](https://discord.com/developers/docs/reference#uploading-files) for details.

###### Autocomplete[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-autocomplete)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>choices</td><td>array of <a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-choice-structure" data-discover="true">choices</a></td><td>autocomplete choices (max of 25 choices)</td></tr></tbody></table>

###### Modal[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-modal)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>custom_id</td><td>string</td><td>Developer-defined identifier for the modal, max 100 characters</td></tr><tr><td>title</td><td>string</td><td>Title of the popup modal, max 45 characters</td></tr><tr><td>components</td><td>array of <a href="https://discord.com/developers/docs/components/reference#component-object" data-discover="true">components</a></td><td>Between 1 and 5 (inclusive) components that make up the modal</td></tr></tbody></table>

If your application responds with user data, you should use [`allowed_mentions`](https://discord.com/developers/docs/resources/message#allowed-mentions-object) to filter which mentions in the content actually ping.

## Interaction Callback[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback)

When responding to an interaction received, you can make a `POST` request to `/interactions/<interaction_id>/<interaction_token>/callback`. `interaction_id` is the unique id of that individual Interaction from the received payload. `interaction_token` is the unique token for that interaction from the received payload.

If you are receiving Interactions over the gateway, you have to respond via HTTP. Responses to Interactions are not sent as commands over the gateway.

If you send this request for an interaction received over HTTP, respond to the original HTTP request with a 202 and no body.

```
import requests

url = "https://discord.com/api/v10/interactions/<interaction_id>/<interaction_token>/callback"

json = {
    "type": 4,
    "data": {
        "content": "Congrats on sending your command!"
    }
}
r = requests.post(url, json=json)
```

Interaction `tokens` are valid for 15 minutes and can be used to send followup messages but you must send an initial response within 3 seconds of receiving the event. If the 3 second deadline is exceeded, the token will be invalidated.

Inline HTTP Response Behavior

###### Interaction Callback Response Object[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-response-object)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>interaction</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-object" data-discover="true">interaction callback object</a></td><td>The interaction object associated with the interaction response.</td></tr><tr><td>resource?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-resource-object" data-discover="true">interaction resource object</a></td><td>The resource that was created by the interaction response.</td></tr></tbody></table>

###### Interaction Callback Object[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-object)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>snowflake</td><td>ID of the interaction</td></tr><tr><td>type</td><td>integer</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type" data-discover="true">Interaction type</a></td></tr><tr><td>activity_instance_id?</td><td>string</td><td>Instance ID of the Activity if one was launched or joined</td></tr><tr><td>response_message_id?</td><td>snowflake</td><td>ID of the message that was created by the interaction</td></tr><tr><td>response_message_loading?</td><td>boolean</td><td>Whether or not the message is in a loading state</td></tr><tr><td>response_message_ephemeral?</td><td>boolean</td><td>Whether or not the response message was ephemeral</td></tr></tbody></table>

###### Interaction Callback Resource Object[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-resource-object)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>type</td><td>integer</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type" data-discover="true">Interaction callback type</a></td></tr><tr><td>activity_instance?*</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-activity-instance-resource" data-discover="true">Activity instance resource</a></td><td>Represents the Activity launched by this interaction.</td></tr><tr><td>message?**</td><td><a href="https://discord.com/developers/docs/resources/message#message-object" data-discover="true">message object</a></td><td>Message created by the interaction.</td></tr></tbody></table>

* Only present if type is `LAUNCH_ACTIVITY`.

** Only present if type is either `CHANNEL_MESSAGE_WITH_SOURCE` or `UPDATE_MESSAGE`.

###### Interaction Callback Activity Instance Resource[](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-activity-instance-resource)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Instance ID of the Activity if one was launched or joined.</td></tr></tbody></table>

## Followup Messages[](https://discord.com/developers/docs/interactions/receiving-and-responding#followup-messages)

Sometimes, your bot will want to send followup messages to a user after responding to an interaction. Or, you may want to edit your original response. Whether you receive Interactions over the gateway or by outgoing webhook, you can use the following endpoints to edit your initial response or send followup messages:

*   [`PATCH /webhooks/<application_id>/<interaction_token>/messages/@original`](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-original-interaction-response) to edit your initial response to an Interaction
*   [`DELETE /webhooks/<application_id>/<interaction_token>/messages/@original`](https://discord.com/developers/docs/interactions/receiving-and-responding#delete-original-interaction-response) to delete your initial response to an Interaction
*   [`POST /webhooks/<application_id>/<interaction_token>`](https://discord.com/developers/docs/interactions/receiving-and-responding#create-followup-message) to send a new followup message
*   [`PATCH /webhooks/<application_id>/<interaction_token>/messages/<message_id>`](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-followup-message) to edit a message sent with that `token`

Interactions webhooks share the same rate limit properties as normal webhooks.

Interaction tokens are valid for 15 minutes, meaning you can respond to an interaction within that amount of time.

### Endpoints[](https://discord.com/developers/docs/interactions/receiving-and-responding#endpoints)

## Create Interaction Response[](https://discord.com/developers/docs/interactions/receiving-and-responding#create-interaction-response)

Create a response to an Interaction. Body is an [interaction response](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object). Returns `204` unless `with_response` is set to `true` which returns `200` with the body as [interaction callback response](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-response-object).

This endpoint also supports file attachments similar to the webhook endpoints. Refer to [Uploading Files](https://discord.com/developers/docs/reference#uploading-files) for details on uploading files and `multipart/form-data` requests.

###### Query String Params[](https://discord.com/developers/docs/interactions/receiving-and-responding#create-interaction-response-query-string-params)

<table><thead><tr><th>Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>with_response?</td><td><a href="https://discord.com/developers/docs/reference#boolean-query-strings" data-discover="true">boolean</a></td><td>Whether to include an <a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-response-object" data-discover="true">interaction callback object</a> as the response</td></tr></tbody></table>

## Get Original Interaction Response[](https://discord.com/developers/docs/interactions/receiving-and-responding#get-original-interaction-response)

Returns the initial Interaction response. Functions the same as [Get Webhook Message](https://discord.com/developers/docs/resources/webhook#get-webhook-message).

## Edit Original Interaction Response[](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-original-interaction-response)

Edits the initial Interaction response. Functions the same as [Edit Webhook Message](https://discord.com/developers/docs/resources/webhook#edit-webhook-message).

## Delete Original Interaction Response[](https://discord.com/developers/docs/interactions/receiving-and-responding#delete-original-interaction-response)

Deletes the initial Interaction response. Returns `204 No Content` on success.

## Create Followup Message[](https://discord.com/developers/docs/interactions/receiving-and-responding#create-followup-message)

Apps are limited to 5 followup messages per interaction if it was initiated from a user-installed app and isn't installed in the server (meaning the [authorizing integration owners object](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-authorizing-integration-owners-object) only contains `USER_INSTALL`)

Create a followup message for an Interaction. Functions the same as [Execute Webhook](https://discord.com/developers/docs/resources/webhook#execute-webhook), but `wait` is always true. The `thread_id`, `avatar_url`, and `username` parameters are not supported when using this endpoint for interaction followups. You can use the `EPHEMERAL` [message flag](https://discord.com/developers/docs/resources/message#message-object-message-flags) `1 << 6` (64) to send a message that only the user can see. You can also use the `IS_COMPONENTS_V2` [message flag](https://discord.com/developers/docs/resources/message#message-object-message-flags) `1 << 15` (32768) to send a [component](https://discord.com/developers/docs/components/reference)-based message.

When using this endpoint directly after responding to an interaction with `DEFERRED_CHANNEL_MESSAGE_WITH_SOURCE`, this endpoint will function as [Edit Original Interaction Response](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-original-interaction-response) for backwards compatibility. In this case, no new message will be created, and the loading message will be edited instead. The ephemeral flag will be ignored, and the value you provided in the initial defer response will be preserved, as an existing message's ephemeral state cannot be changed. This behavior is deprecated, and you should use the Edit Original Interaction Response endpoint in this case instead.

## Get Followup Message[](https://discord.com/developers/docs/interactions/receiving-and-responding#get-followup-message)

Returns a followup message for an Interaction. Functions the same as [Get Webhook Message](https://discord.com/developers/docs/resources/webhook#get-webhook-message).

## Edit Followup Message[](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-followup-message)

Edits a followup message for an Interaction. Functions the same as [Edit Webhook Message](https://discord.com/developers/docs/resources/webhook#edit-webhook-message).

## Delete Followup Message[](https://discord.com/developers/docs/interactions/receiving-and-responding#delete-followup-message)

Deletes a followup message for an Interaction. Returns `204 No Content` on success.