---
url: https://discordpy.readthedocs.io/en/stable/interactions/api.html
time: 2025-09-21P23:27:57
tags: 
---
The following section outlines the API of interactions, as implemented by the library.

For documentation about the rest of the library, check [API Reference](https://discordpy.readthedocs.io/en/stable/api.html).

## Models[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#models "Permalink to this headline")

Similar to [Discord Models](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-models), these are not meant to be constructed by the user.

### Interaction[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#interaction "Permalink to this headline")

_class_ discord.Interaction[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "Permalink to this definition")

Represents a Discord interaction.

An interaction happens when a user does an action that needs to be notified. Current examples are slash commands and components.

New in version 2.0.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.id "Permalink to this definition")

The interaction’s ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.type "Permalink to this definition")

The interaction type.

Type

[`InteractionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType "discord.InteractionType")

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.guild_id "Permalink to this definition")

The guild ID the interaction was sent from.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

channel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.channel "Permalink to this definition")

The channel the interaction was sent from.

Note that due to a Discord limitation, if sent from a DM channel [`recipient`](https://discordpy.readthedocs.io/en/stable/api.html#discord.DMChannel.recipient "discord.DMChannel.recipient") is `None`.

Type

Optional[Union[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel"), [`abc.PrivateChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.PrivateChannel "discord.abc.PrivateChannel"), [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")]]

entitlement_sku_ids[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.entitlement_sku_ids "Permalink to this definition")

The entitlement SKU IDs that the user has.

Type

List[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

entitlements[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.entitlements "Permalink to this definition")

The entitlements that the guild or user has.

Type

List[[`Entitlement`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Entitlement "discord.Entitlement")]

application_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.application_id "Permalink to this definition")

The application ID that the interaction was for.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.user "Permalink to this definition")

The user or member that sent the interaction.

Type

Union[[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User"), [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member")]

message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.message "Permalink to this definition")

The message that sent this interaction.

This is only available for [`InteractionType.component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.component "discord.InteractionType.component") interactions.

Type

Optional[[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")]

token[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.token "Permalink to this definition")

The token to continue the interaction. These are valid for 15 minutes.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

data[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.data "Permalink to this definition")

The raw interaction data.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

locale[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.locale "Permalink to this definition")

The locale of the user invoking the interaction.

Type

[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale")

guild_locale[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.guild_locale "Permalink to this definition")

The preferred locale of the guild the interaction was sent from, if any.

Type

Optional[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale")]

A dictionary that can be used to store extraneous data for use during interaction processing. The library will not touch any values or keys within this dictionary.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

command_failed[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.command_failed "Permalink to this definition")

Whether the command associated with this interaction failed to execute. This includes checks and execution.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

context[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.context "Permalink to this definition")

The context of the interaction.

New in version 2.4.

Type

[`AppCommandContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "discord.app_commands.AppCommandContext")

filesize_limit[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.filesize_limit "Permalink to this definition")

The maximum number of bytes a file can have when responding to this interaction.

New in version 2.6.

Type

[int](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_property_ client[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.client "Permalink to this definition")

The client that is handling this interaction.

Note that [`AutoShardedClient`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AutoShardedClient "discord.AutoShardedClient"), [`Bot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot "discord.ext.commands.Bot"), and [`AutoShardedBot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.AutoShardedBot "discord.ext.commands.AutoShardedBot") are all subclasses of client.

Type

[`Client`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client "discord.Client")

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.guild "Permalink to this definition")

The guild the interaction was sent from.

Type

Optional[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

_property_ channel_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.channel_id "Permalink to this definition")

The ID of the channel the interaction was sent from.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.permissions "Permalink to this definition")

The resolved permissions of the member in the channel, including overwrites.

In a non-guild context where this doesn’t apply, an empty permissions object is returned.

Type

[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")

_property_ app_permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.app_permissions "Permalink to this definition")

The resolved permissions of the application or the bot, including overwrites.

Type

[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")

namespace[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.namespace "Permalink to this definition")

The resolved namespace for this interaction.

If the interaction is not an application command related interaction or the client does not have a tree attached to it then this returns an empty namespace.

Type

[`app_commands.Namespace`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Namespace "discord.app_commands.Namespace")

command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.command "Permalink to this definition")

The command being called from this interaction.

If the interaction is not an application command related interaction or the command is not found in the client’s attached tree then `None` is returned.

Type

Optional[Union[[`app_commands.Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`app_commands.ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu")]]

response[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.response "Permalink to this definition")

Returns an object responsible for handling responding to the interaction.

A response can only be done once. If secondary messages need to be sent, consider using [`followup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.followup "discord.Interaction.followup") instead.

Type

[`InteractionResponse`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse "discord.InteractionResponse")

followup[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.followup "Permalink to this definition")

Returns the follow up webhook for follow up interactions.

Type

[`Webhook`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Webhook "discord.Webhook")

_property_ created_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.created_at "Permalink to this definition")

When the interaction was created.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

_property_ expires_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.expires_at "Permalink to this definition")

When the interaction expires.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

is_expired()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.is_expired "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Returns `True` if the interaction is expired.

is_guild_integration()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.is_guild_integration "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Returns `True` if the interaction is a guild integration.

New in version 2.4.

is_user_integration()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.is_user_integration "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Returns `True` if the interaction is a user integration.

New in version 2.4.

_await_ original_response()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.original_response "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Fetches the original interaction response message associated with the interaction.

If the interaction response was a newly created message (i.e. through [`InteractionResponse.send_message()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_message "discord.InteractionResponse.send_message") or [`InteractionResponse.defer()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.defer "discord.InteractionResponse.defer"), where `thinking` is `True`) then this returns the message that was sent using that response. Otherwise, this returns the message that triggered the interaction (i.e. through a component).

Repeated calls to this will return a cached value.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the original response message failed.
    
*   [**ClientException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientException "discord.ClientException") – The channel for the message could not be resolved.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The interaction response message does not exist.
    

Returns

The original interaction response message.

Return type

[InteractionMessage](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage")

_await_ edit_original_response(_*_, _content=..._, _embeds=..._, _embed=..._, _attachments=..._, _view=..._, _allowed_mentions=None_, _poll=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.edit_original_response "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Edits the original interaction response message.

This is a lower level interface to [`InteractionMessage.edit()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.edit "discord.InteractionMessage.edit") in case you do not want to fetch the message and save an HTTP request.

This method is also the only way to edit the original message if the message sent was ephemeral.

Parameters

*   **content** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The content to edit the message with or `None` to clear it.
    
*   **embeds** (List[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – A list of embeds to edit the message with.
    
*   **embed** (Optional[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – The embed to edit the message with. `None` suppresses the embeds. This should not be mixed with the `embeds` parameter.
    
*   **attachments** (List[Union[[`Attachment`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Attachment "discord.Attachment"), [`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")]]) –
    
    A list of attachments to keep in the message as well as new files to upload. If `[]` is passed then all attachments are removed.
    
    Note
    
    New files will always appear after current attachments.
    
*   **allowed_mentions** ([`AllowedMentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions "discord.AllowedMentions")) – Controls the mentions being processed in this message. See [`abc.Messageable.send()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable.send "discord.abc.Messageable.send") for more information.
    
*   **view** (Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]) –
    
    The updated view to update this message with. If `None` is passed then the view is removed.
    
    Note
    
    If you want to update the message to have a [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView"), you must explicitly set the `content`, `embed`, `embeds`, and `attachments` parameters to `None` if the previous message had any.
    
*   **poll** ([`Poll`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Poll "discord.Poll")) –
    
    The poll to create when editing the message.
    
    New in version 2.5.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Editing the message failed.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The interaction response message does not exist.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – Edited a message that is not yours.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – You specified both `embed` and `embeds`
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The length of `embeds` was invalid.
    

Returns

The newly edited message.

Return type

[`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage")

_await_ delete_original_response()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.delete_original_response "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Deletes the original interaction response message.

This is a lower level interface to [`InteractionMessage.delete()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.delete "discord.InteractionMessage.delete") in case you do not want to fetch the message and save an HTTP request.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Deleting the message failed.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The interaction response message does not exist or has already been deleted.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – Deleted a message that is not yours.
    

_await_ translate(_string_, _*_, _locale=..._, _data=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.translate "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Translates a string using the set [`Translator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "discord.app_commands.Translator").

New in version 2.1.

Parameters

*   **string** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The string to translate. [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") can be used to add more context, information, or any metadata necessary.
    
*   **locale** ([`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale")) – The locale to use, this is handy if you want the translation for a specific locale. Defaults to the user’s [`locale`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.locale "discord.Interaction.locale").
    
*   **data** (_Any_) – The extraneous data that is being translated. If not specified, either [`command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.command "discord.Interaction.command") or [`message`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.message "discord.Interaction.message") will be passed, depending on which is available in the context.
    

Returns

The translated string, or `None` if a translator was not set.

Return type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

### InteractionResponse[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#interactionresponse "Permalink to this headline")

_class_ discord.InteractionResponse[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse "Permalink to this definition")

Represents a Discord interaction response.

This type can be accessed through [`Interaction.response`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.response "discord.Interaction.response").

New in version 2.0.

is_done()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.is_done "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Indicates whether an interaction response has been done before.

An interaction can only be responded to once.

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.type "Permalink to this definition")

The type of response that was sent, `None` if response is not done.

Type

[`InteractionResponseType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType "discord.InteractionResponseType")

_await_ defer(_*_, _ephemeral=False_, _thinking=False_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.defer "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Defers the interaction response.

This is typically used when the interaction is acknowledged and a secondary action will be done later.

This is only supported with the following interaction types:

*   [`InteractionType.application_command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.application_command "discord.InteractionType.application_command")
    
*   [`InteractionType.component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.component "discord.InteractionType.component")
    
*   [`InteractionType.modal_submit`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.modal_submit "discord.InteractionType.modal_submit")
    

Parameters

*   **ephemeral** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates whether the deferred message will eventually be ephemeral. This only applies to [`InteractionType.application_command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.application_command "discord.InteractionType.application_command") interactions, or if `thinking` is `True`.
    
*   **thinking** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates whether the deferred type should be [`InteractionResponseType.deferred_channel_message`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.deferred_channel_message "discord.InteractionResponseType.deferred_channel_message") instead of the default [`InteractionResponseType.deferred_message_update`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.deferred_message_update "discord.InteractionResponseType.deferred_message_update") if both are valid. In UI terms, this is represented as if the bot is thinking of a response. It is your responsibility to eventually send a followup message via [`Interaction.followup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.followup "discord.Interaction.followup") to make this thinking state go away. Application commands (AKA Slash commands) cannot use [`InteractionResponseType.deferred_message_update`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.deferred_message_update "discord.InteractionResponseType.deferred_message_update").
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Deferring the interaction failed.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

Returns

The interaction callback resource, or `None`.

Return type

Optional[[`InteractionCallbackResponse`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse "discord.InteractionCallbackResponse")]

_await_ pong()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.pong "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Pongs the ping interaction.

This should rarely be used.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Ponging the interaction failed.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

_await_ send_message(_content=None_, _*_, _embed=..._, _embeds=..._, _file=..._, _files=..._, _view=..._, _tts=False_, _ephemeral=False_, _allowed_mentions=..._, _suppress_embeds=False_, _silent=False_, _delete_after=None_, _poll=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_message "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Responds to this interaction by sending a message.

Parameters

*   **content** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The content of the message to send.
    
*   **embeds** (List[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – A list of embeds to send with the content. Maximum of 10. This cannot be mixed with the `embed` parameter.
    
*   **embed** ([`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")) – The rich embed for the content to send. This cannot be mixed with `embeds` parameter.
    
*   **file** ([`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")) – The file to upload.
    
*   **files** (List[[`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")]) – A list of files to upload. Must be a maximum of 10.
    
*   **tts** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates if the message should be sent using text-to-speech.
    
*   **view** (Union[[`discord.ui.View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`discord.ui.LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]) – The view to send with the message.
    
*   **ephemeral** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates if the message should only be visible to the user who started the interaction. If a view is sent with an ephemeral message and it has no timeout set then the timeout is set to 15 minutes.
    
*   **allowed_mentions** ([`AllowedMentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions "discord.AllowedMentions")) – Controls the mentions being processed in this message. See [`abc.Messageable.send()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable.send "discord.abc.Messageable.send") for more information.
    
*   **suppress_embeds** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to suppress embeds for the message. This sends the message without any embeds if set to `True`.
    
*   **silent** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to suppress push and desktop notifications for the message. This will increment the mention counter in the UI, but will not actually send a notification.
    
    New in version 2.2.
    
*   **delete_after** ([`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")) –
    
    If provided, the number of seconds to wait in the background before deleting the message we just sent. If the deletion fails, then it is silently ignored.
    
    New in version 2.1.
    
*   **poll** ([`Poll`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Poll "discord.Poll")) –
    
    The poll to send with this message.
    
    New in version 2.4.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Sending the message failed.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – You specified both `embed` and `embeds` or `file` and `files`.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The length of `embeds` was invalid.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

Returns

The interaction callback data.

Return type

[`InteractionCallbackResponse`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse "discord.InteractionCallbackResponse")

_await_ edit_message(_*_, _content=..._, _embed=..._, _embeds=..._, _attachments=..._, _view=..._, _allowed_mentions=..._, _delete_after=None_, _suppress_embeds=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.edit_message "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Responds to this interaction by editing the original message of a component or modal interaction.

Parameters

*   **content** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The new content to replace the message with. `None` removes the content.
    
*   **embeds** (List[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – A list of embeds to edit the message with.
    
*   **embed** (Optional[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – The embed to edit the message with. `None` suppresses the embeds. This should not be mixed with the `embeds` parameter.
    
*   **attachments** (List[Union[[`Attachment`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Attachment "discord.Attachment"), [`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")]]) –
    
    A list of attachments to keep in the message as well as new files to upload. If `[]` is passed then all attachments are removed.
    
    Note
    
    New files will always appear after current attachments.
    
*   **view** (Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]) –
    
    The updated view to update this message with. If `None` is passed then the view is removed.
    
    Note
    
    To update the message to add a [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView"), you must explicitly set the `content`, `embed`, `embeds`, and `attachments` parameters to either `None` or an empty array, as appropriate.
    
*   **allowed_mentions** (Optional[[`AllowedMentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions "discord.AllowedMentions")]) – Controls the mentions being processed in this message. See [`Message.edit()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.edit "discord.Message.edit") for more information.
    
*   **delete_after** ([`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")) –
    
    If provided, the number of seconds to wait in the background before deleting the message we just edited. If the deletion fails, then it is silently ignored.
    
    New in version 2.2.
    
*   **suppress_embeds** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to suppress embeds for the message. This removes all the embeds if set to `True`. If set to `False` this brings the embeds back if they were suppressed. Using this parameter requires [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages").
    
    New in version 2.4.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Editing the message failed.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – You specified both `embed` and `embeds`.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

Returns

The interaction callback data, or `None` if editing the message was not possible.

Return type

Optional[[`InteractionCallbackResponse`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse "discord.InteractionCallbackResponse")]

_await_ send_modal(_modal_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_modal "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Responds to this interaction by sending a modal.

Parameters

**modal** ([`Modal`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal "discord.ui.Modal")) – The modal to send.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Sending the modal failed.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

Returns

The interaction callback data.

Return type

[`InteractionCallbackResponse`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse "discord.InteractionCallbackResponse")

_await_ autocomplete(_choices_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.autocomplete "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Responds to this interaction by giving the user the choices they can use.

Parameters

**choices** (List[[`Choice`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "discord.app_commands.Choice")]) – The list of new choices as the user is typing.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Sending the choices failed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – This interaction cannot respond with autocomplete.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

_await_ launch_activity()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.launch_activity "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Responds to this interaction by launching the activity associated with the app. Only available for apps with activities enabled.

New in version 2.6.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Launching the activity failed.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

Returns

The interaction callback data.

Return type

[`InteractionCallbackResponse`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse "discord.InteractionCallbackResponse")

### InteractionCallbackResponse[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#interactioncallbackresponse "Permalink to this headline")

_class_ discord.InteractionCallbackResponse[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse "Permalink to this definition")

Represents an interaction response callback.

New in version 2.5.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.id "Permalink to this definition")

The interaction ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.type "Permalink to this definition")

The interaction callback response type.

Type

[`InteractionResponseType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType "discord.InteractionResponseType")

resource[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.resource "Permalink to this definition")

The resource that the interaction response created. If a message was sent, this will be a [`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage"). If an activity was launched this will be a [`InteractionCallbackActivityInstance`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackActivityInstance "discord.InteractionCallbackActivityInstance"). In any other case, this will be `None`.

Type

Optional[Union[[`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage"), [`InteractionCallbackActivityInstance`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackActivityInstance "discord.InteractionCallbackActivityInstance")]]

message_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.message_id "Permalink to this definition")

The message ID of the resource. Only available if the resource is a [`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage").

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

activity_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.activity_id "Permalink to this definition")

The activity ID of the resource. Only available if the resource is a [`InteractionCallbackActivityInstance`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackActivityInstance "discord.InteractionCallbackActivityInstance").

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

is_thinking()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.is_thinking "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the response was a thinking defer.

is_ephemeral()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackResponse.is_ephemeral "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the response was ephemeral.

### InteractionCallbackActivityInstance[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#interactioncallbackactivityinstance "Permalink to this headline")

_class_ discord.InteractionCallbackActivityInstance[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackActivityInstance "Permalink to this definition")

Represents an activity instance launched as an interaction response.

New in version 2.5.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionCallbackActivityInstance.id "Permalink to this definition")

The activity instance ID.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

### InteractionMessage[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#interactionmessage "Permalink to this headline")

_class_ discord.InteractionMessage[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "Permalink to this definition")

Represents the original interaction response message.

This allows you to edit or delete the message associated with the interaction response. To retrieve this object see [`Interaction.original_response()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.original_response "discord.Interaction.original_response").

This inherits from [`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") with changes to [`edit()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.edit "discord.InteractionMessage.edit") and [`delete()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.delete "discord.InteractionMessage.delete") to work.

New in version 2.0.

_await_ add_reaction(_emoji_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.add_reaction "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Adds a reaction to the message.

The emoji may be a unicode emoji or a custom guild [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji").

You must have [`read_message_history`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.read_message_history "discord.Permissions.read_message_history") to do this. If nobody else has reacted to the message using this emoji, [`add_reactions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.add_reactions "discord.Permissions.add_reactions") is required.

Changed in version 2.0: `emoji` parameter is now positional-only.

Changed in version 2.0: This function will now raise [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") instead of `InvalidArgument`.

Parameters

**emoji** (Union[[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`Reaction`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Reaction "discord.Reaction"), [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The emoji to react with.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Adding the reaction failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to react to the message.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The emoji you specified was not found.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The emoji parameter is invalid.
    

clean_content[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.clean_content "Permalink to this definition")

A property that returns the content in a “cleaned up” manner. This basically means that mentions are transformed into the way the client shows it. e.g. `<#id>` will transform into `#name`.

This will also transform @everyone and @here mentions into non-mentions.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_await_ clear_reaction(_emoji_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.clear_reaction "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Clears a specific reaction from the message.

The emoji may be a unicode emoji or a custom guild [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji").

You must have [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") to do this.

New in version 1.3.

Changed in version 2.0: This function will now raise [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") instead of `InvalidArgument`.

Parameters

**emoji** (Union[[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`Reaction`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Reaction "discord.Reaction"), [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The emoji to clear.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Clearing the reaction failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to clear the reaction.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The emoji you specified was not found.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The emoji parameter is invalid.
    

_await_ clear_reactions()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.clear_reactions "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Removes all the reactions from the message.

You must have [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") to do this.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Removing the reactions failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to remove all the reactions.
    

_await_ create_thread(_*_, _name_, _auto_archive_duration=..._, _slowmode_delay=None_, _reason=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.create_thread "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Creates a public thread from this message.

You must have [`create_public_threads`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.create_public_threads "discord.Permissions.create_public_threads") in order to create a public thread from a message.

The channel this message belongs in must be a [`TextChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.TextChannel "discord.TextChannel").

New in version 2.0.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the thread.
    
*   **auto_archive_duration** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) –
    
    The duration in minutes before a thread is automatically hidden from the channel list. If not provided, the channel’s default auto archive duration is used.
    
    Must be one of `60`, `1440`, `4320`, or `10080`, if provided.
    
*   **slowmode_delay** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – Specifies the slowmode rate limit for user in this channel, in seconds. The maximum value possible is `21600`. By default no slowmode rate limit if this is `None`.
    
*   **reason** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The reason for creating a new thread. Shows up on the audit log.
    

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permissions to create a thread.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Creating the thread failed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – This message does not have guild info attached.
    

Returns

The created thread.

Return type

[`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")

_property_ created_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.created_at "Permalink to this definition")

The message’s creation time in UTC.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

_await_ edit(_*_, _content=..._, _embeds=..._, _embed=..._, _attachments=..._, _view=..._, _allowed_mentions=None_, _delete_after=None_, _poll=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.edit "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Edits the message.

Parameters

*   **content** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The content to edit the message with or `None` to clear it.
    
*   **embeds** (List[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – A list of embeds to edit the message with.
    
*   **embed** (Optional[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) – The embed to edit the message with. `None` suppresses the embeds. This should not be mixed with the `embeds` parameter.
    
*   **attachments** (List[Union[[`Attachment`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Attachment "discord.Attachment"), [`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")]]) –
    
    A list of attachments to keep in the message as well as new files to upload. If `[]` is passed then all attachments are removed.
    
    Note
    
    New files will always appear after current attachments.
    
*   **allowed_mentions** ([`AllowedMentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions "discord.AllowedMentions")) – Controls the mentions being processed in this message. See [`abc.Messageable.send()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable.send "discord.abc.Messageable.send") for more information.
    
*   **view** (Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]) –
    
    The updated view to update this message with. If `None` is passed then the view is removed.
    
    Note
    
    If you want to update the message to have a [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView"), you must explicitly set the `content`, `embed`, `embeds`, and `attachments` parameters to `None` if the previous message had any.
    
*   **delete_after** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) –
    
    If provided, the number of seconds to wait in the background before deleting the message we just sent. If the deletion fails, then it is silently ignored.
    
    New in version 2.2.
    
*   **poll** ([`Poll`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Poll "discord.Poll")) –
    
    The poll to create when editing the message.
    
    New in version 2.5.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Editing the message failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – Edited a message that is not yours.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – You specified both `embed` and `embeds`
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The length of `embeds` was invalid.
    

Returns

The newly edited message.

Return type

[`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage")

_property_ edited_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.edited_at "Permalink to this definition")

An aware UTC datetime object containing the edited time of the message.

Type

Optional[[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]

_await_ end_poll()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.end_poll "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Ends the [`Poll`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Poll "discord.Poll") attached to this message.

This can only be done if you are the message author.

If the poll was successfully ended, then it returns the updated [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message").

Raises

[**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Ending the poll failed.

Returns

The updated message.

Return type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

_await_ fetch()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.fetch "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Fetches the partial message to a full [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message").

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The message was not found.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the permissions required to get a message.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the message failed.
    

Returns

The full message.

Return type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

_await_ fetch_thread()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.fetch_thread "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves the public thread attached to this message.

Note

This method is an API call. For general usage, consider [`thread`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.thread "discord.InteractionMessage.thread") instead.

New in version 2.4.

Raises

*   [**InvalidData**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InvalidData "discord.InvalidData") – An unknown channel type was received from Discord or the guild the thread belongs to is not the same as the one in this object points to.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the thread failed.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – There is no thread attached to this message.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permission to fetch this channel.
    

Returns

The public thread attached to this message.

Return type

[`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")

_await_ forward(_destination_, _*_, _fail_if_not_exists=True_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.forward "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Forwards this message to a channel.

New in version 2.5.

Parameters

*   **destination** ([`Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable")) – The channel to forward this message to.
    
*   **fail_if_not_exists** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether replying using the message reference should raise [`HTTPException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") if the message no longer exists or Discord could not fetch the message.
    

Raises

[**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Forwarding the message failed.

Returns

The message sent to the channel.

Return type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

_property_ interaction[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.interaction "Permalink to this definition")

The interaction that this message is a response to.

New in version 2.0.

Deprecated since version 2.4: This attribute is deprecated and will be removed in a future version. Use [`interaction_metadata`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.interaction_metadata "discord.Message.interaction_metadata") instead.

Type

Optional[[`MessageInteraction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction "discord.MessageInteraction")]

is_system()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.is_system "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the message is a system message.

A system message is a message that is constructed entirely by the Discord API in response to something.

New in version 1.3.

_property_ jump_url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.jump_url "Permalink to this definition")

Returns a URL that allows the client to jump to this message.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_await_ pin(_*_, _reason=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.pin "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Pins the message.

You must have [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") to do this in a non-private channel context.

Parameters

**reason** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) –

The reason for pinning the message. Shows up on the audit log.

New in version 1.4.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permissions to pin the message.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The message or channel was not found or deleted.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Pinning the message failed, probably due to the channel having more than 50 pinned messages.
    

_property_ pinned_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.pinned_at "Permalink to this definition")

An aware UTC datetime object containing the time when the message was pinned.

New in version 2.6.

Type

Optional[[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]

_await_ publish()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.publish "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Publishes this message to the channel’s followers.

The message must have been sent in a news channel. You must have [`send_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.send_messages "discord.Permissions.send_messages") to do this.

If the message is not your own then [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") is also needed.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to publish this message or the channel is not a news channel.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Publishing the message failed.
    

raw_channel_mentions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.raw_channel_mentions "Permalink to this definition")

A property that returns an array of channel IDs matched with the syntax of `<#channel_id>` in the message content.

Type

List[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

raw_mentions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.raw_mentions "Permalink to this definition")

A property that returns an array of user IDs matched with the syntax of `<@user_id>` in the message content.

This allows you to receive the user IDs of mentioned users even in a private message context.

Type

List[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

raw_role_mentions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.raw_role_mentions "Permalink to this definition")

A property that returns an array of role IDs matched with the syntax of `<@&role_id>` in the message content.

Type

List[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_await_ remove_reaction(_emoji_, _member_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.remove_reaction "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Remove a reaction by the member from the message.

The emoji may be a unicode emoji or a custom guild [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji").

If the reaction is not your own (i.e. `member` parameter is not you) then [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") is needed.

The `member` parameter must represent a member and meet the [`abc.Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake") abc.

Changed in version 2.0: This function will now raise [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") instead of `InvalidArgument`.

Parameters

*   **emoji** (Union[[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`Reaction`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Reaction "discord.Reaction"), [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The emoji to remove.
    
*   **member** ([`abc.Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The member for which to remove the reaction.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Removing the reaction failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to remove the reaction.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The member or emoji you specified was not found.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The emoji parameter is invalid.
    

_await_ reply(_content=None_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.reply "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A shortcut method to [`abc.Messageable.send()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable.send "discord.abc.Messageable.send") to reply to the [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message").

New in version 1.6.

Changed in version 2.0: This function will now raise [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") or [`ValueError`](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") instead of `InvalidArgument`.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Sending the message failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to send the message.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The `files` list is not of the appropriate size
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – You specified both `file` and `files`.
    

Returns

The message that was sent.

Return type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

system_content[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.system_content "Permalink to this definition")

A property that returns the content that is rendered regardless of the [`Message.type`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.type "discord.Message.type").

In the case of [`MessageType.default`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageType.default "discord.MessageType.default") and [`MessageType.reply`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageType.reply "discord.MessageType.reply"), this just returns the regular [`Message.content`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.content "discord.Message.content"). Otherwise this returns an English message denoting the contents of the system message.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ thread[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.thread "Permalink to this definition")

The public thread created from this message, if it exists.

Note

For messages received via the gateway this does not retrieve archived threads, as they are not retained in the internal cache. Use [`fetch_thread()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.fetch_thread "discord.InteractionMessage.fetch_thread") instead.

New in version 2.4.

Type

Optional[[`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")]

to_reference(_*_, _fail_if_not_exists=True_, _type=<MessageReferenceType.default: 0>_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.to_reference "Permalink to this definition")

Creates a [`MessageReference`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageReference "discord.MessageReference") from the current message.

New in version 1.6.

Parameters

*   **fail_if_not_exists** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the referenced message should raise [`HTTPException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") if the message no longer exists or Discord could not fetch the message.
    
    New in version 1.7.
    
*   **type** ([`MessageReferenceType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageReferenceType "discord.MessageReferenceType")) –
    
    The type of message reference.
    
    New in version 2.5.
    

Returns

The reference to this message.

Return type

[`MessageReference`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageReference "discord.MessageReference")

_await_ unpin(_*_, _reason=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.unpin "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Unpins the message.

You must have [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") to do this in a non-private channel context.

Parameters

**reason** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) –

The reason for unpinning the message. Shows up on the audit log.

New in version 1.4.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permissions to unpin the message.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The message or channel was not found or deleted.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Unpinning the message failed.
    

_await_ add_files(_*files_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.add_files "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Adds new files to the end of the message attachments.

New in version 2.0.

Parameters

***files** ([`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")) – New files to add to the message.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Editing the message failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – Tried to edit a message that isn’t yours.
    

Returns

The newly edited message.

Return type

[`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage")

_await_ remove_attachments(_*attachments_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.remove_attachments "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Removes attachments from the message.

New in version 2.0.

Parameters

***attachments** ([`Attachment`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Attachment "discord.Attachment")) – Attachments to remove from the message.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Editing the message failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – Tried to edit a message that isn’t yours.
    

Returns

The newly edited message.

Return type

[`InteractionMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage "discord.InteractionMessage")

_await_ delete(_*_, _delay=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionMessage.delete "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Deletes the message.

Parameters

**delay** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – If provided, the number of seconds to wait before deleting the message. The waiting is done in the background and deletion failures are ignored.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have proper permissions to delete the message.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The message was deleted already.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Deleting the message failed.
    

### MessageInteraction[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#messageinteraction "Permalink to this headline")

_class_ discord.MessageInteraction[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction "Permalink to this definition")

Represents the interaction that a [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") is a response to.

New in version 2.0.

x == y

Checks if two message interactions are equal.

x != y

Checks if two message interactions are not equal.

hash(x)

Returns the message interaction’s hash.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction.id "Permalink to this definition")

The interaction ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction.type "Permalink to this definition")

The interaction type.

Type

[`InteractionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType "discord.InteractionType")

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction.name "Permalink to this definition")

The name of the interaction.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction.user "Permalink to this definition")

The user or member that invoked the interaction.

Type

Union[[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User"), [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member")]

_property_ created_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteraction.created_at "Permalink to this definition")

The interaction’s creation time in UTC.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

### MessageInteractionMetadata[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#messageinteractionmetadata "Permalink to this headline")

_class_ discord.MessageInteractionMetadata[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata "Permalink to this definition")

Represents the interaction metadata of a [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") if it was sent in response to an interaction.

New in version 2.4.

x == y

Checks if two message interactions are equal.

x != y

Checks if two message interactions are not equal.

hash(x)

Returns the message interaction’s hash.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.id "Permalink to this definition")

The interaction ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.type "Permalink to this definition")

The interaction type.

Type

[`InteractionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType "discord.InteractionType")

user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.user "Permalink to this definition")

The user that invoked the interaction.

Type

[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User")

original_response_message_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.original_response_message_id "Permalink to this definition")

The ID of the original response message if the message is a follow-up.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

interacted_message_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.interacted_message_id "Permalink to this definition")

The ID of the message that containes the interactive components, if applicable.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

modal_interaction[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.modal_interaction "Permalink to this definition")

The metadata of the modal submit interaction that triggered this interaction, if applicable.

Type

Optional[[`MessageInteractionMetadata`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata "discord.MessageInteractionMetadata")]

target_user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.target_user "Permalink to this definition")

The user the command was run on, only applicable to user context menus.

New in version 2.5.

Type

Optional[[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User")]

target_message_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.target_message_id "Permalink to this definition")

The ID of the message the command was run on, only applicable to message context menus.

New in version 2.5.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ created_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.created_at "Permalink to this definition")

The interaction’s creation time in UTC.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

_property_ original_response_message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.original_response_message "Permalink to this definition")

The original response message if the message is a follow-up and is found in cache.

Type

Optional[[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")]

_property_ interacted_message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.interacted_message "Permalink to this definition")

The message that containes the interactive components, if applicable and is found in cache.

Type

Optional[[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")]

_property_ target_message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.target_message "Permalink to this definition")

The target message, if applicable and is found in cache.

New in version 2.5.

Type

Optional[[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")]

is_guild_integration()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.is_guild_integration "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Returns `True` if the interaction is a guild integration.

is_user_integration()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MessageInteractionMetadata.is_user_integration "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Returns `True` if the interaction is a user integration.

### Component[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#component "Permalink to this headline")

_class_ discord.Component[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "Permalink to this definition")

Represents a Discord Bot UI Kit Component.

The components supported by Discord are:

*   [`ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ActionRow "discord.ActionRow")
    
*   [`Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button "discord.Button")
    
*   [`SelectMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectMenu "discord.SelectMenu")
    
*   [`TextInput`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput "discord.TextInput")
    
*   [`SectionComponent`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent "discord.SectionComponent")
    
*   [`TextDisplay`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay "discord.TextDisplay")
    
*   [`ThumbnailComponent`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent "discord.ThumbnailComponent")
    
*   [`MediaGalleryComponent`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent "discord.MediaGalleryComponent")
    
*   [`FileComponent`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent "discord.FileComponent")
    
*   [`SeparatorComponent`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent "discord.SeparatorComponent")
    
*   [`Container`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container "discord.Container")
    

This class is abstract and cannot be instantiated.

New in version 2.0.

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### ActionRow[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#actionrow "Permalink to this headline")

_class_ discord.ActionRow[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ActionRow "Permalink to this definition")

Represents a Discord Bot UI Kit Action Row.

This is a component that holds up to 5 children components in a row.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

New in version 2.0.

children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ActionRow.children "Permalink to this definition")

The children components that this holds, if any.

Type

List[Union[[`Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button "discord.Button"), [`SelectMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectMenu "discord.SelectMenu"), [`TextInput`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput "discord.TextInput")]]

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ActionRow.id "Permalink to this definition")

The ID of this component.

New in version 2.6.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ActionRow.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### Button[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#button "Permalink to this headline")

_class_ discord.Button[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button "Permalink to this definition")

Represents a button from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type to create a button is [`discord.ui.Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button") not this one.

New in version 2.0.

style[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.style "Permalink to this definition")

The style of the button.

Type

[`ButtonStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle "discord.ButtonStyle")

custom_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.custom_id "Permalink to this definition")

The ID of the button that gets received during an interaction. If this button is for a URL, it does not have a custom ID.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.url "Permalink to this definition")

The URL this button sends you to.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

disabled[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.disabled "Permalink to this definition")

Whether the button is disabled or not.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.label "Permalink to this definition")

The label of the button, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

emoji[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.emoji "Permalink to this definition")

The emoji of the button, if available.

Type

Optional[[`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji")]

sku_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.sku_id "Permalink to this definition")

The SKU ID this button sends you to, if available.

New in version 2.4.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.id "Permalink to this definition")

The ID of this component.

New in version 2.6.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Button.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### TextInput[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#textinput "Permalink to this headline")

_class_ discord.TextInput[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput "Permalink to this definition")

Represents a text input from the Discord Bot UI Kit.

Note

The user constructible and usable type to create a text input is [`discord.ui.TextInput`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput "discord.ui.TextInput") not this one.

New in version 2.0.

custom_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.custom_id "Permalink to this definition")

The ID of the text input that gets received during an interaction.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.label "Permalink to this definition")

The label to display above the text input.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

style[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.style "Permalink to this definition")

The style of the text input.

Type

[`TextStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle "discord.TextStyle")

placeholder[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.placeholder "Permalink to this definition")

The placeholder text to display when the text input is empty.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.value "Permalink to this definition")

The default value of the text input.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

required[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.required "Permalink to this definition")

Whether the text input is required.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

min_length[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.min_length "Permalink to this definition")

The minimum length of the text input.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

max_length[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.max_length "Permalink to this definition")

The maximum length of the text input.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.id "Permalink to this definition")

The ID of this component.

New in version 2.6.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

_property_ default[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.default "Permalink to this definition")

The default value of the text input.

This is an alias to [`value`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextInput.value "discord.TextInput.value").

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

### LabelComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#labelcomponent "Permalink to this headline")

_class_ discord.LabelComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.LabelComponent "Permalink to this definition")

Represents a label component from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type for creating a label is [`discord.ui.Label`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label "discord.ui.Label") not this one.

New in version 2.6.

label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.LabelComponent.label "Permalink to this definition")

The label text to display.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.LabelComponent.description "Permalink to this definition")

The description text to display below the label, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

component[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.LabelComponent.component "Permalink to this definition")

The component that this label is associated with.

Type

[`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.LabelComponent.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.LabelComponent.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### SectionComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#sectioncomponent "Permalink to this headline")

_class_ discord.SectionComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent "Permalink to this definition")

Represents a section from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type to create a section is [`discord.ui.Section`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section "discord.ui.Section") not this one.

New in version 2.6.

children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent.children "Permalink to this definition")

The components on this section.

Type

List[[`TextDisplay`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay "discord.TextDisplay")]

accessory[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent.accessory "Permalink to this definition")

The section accessory.

Type

[`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SectionComponent.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### ThumbnailComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#thumbnailcomponent "Permalink to this headline")

_class_ discord.ThumbnailComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent "Permalink to this definition")

Represents a Thumbnail from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type to create a thumbnail is [`discord.ui.Thumbnail`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail "discord.ui.Thumbnail") not this one.

New in version 2.6.

media[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent.media "Permalink to this definition")

The media for this thumbnail.

Type

[`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent.description "Permalink to this definition")

The description shown within this thumbnail.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

spoiler[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent.spoiler "Permalink to this definition")

Whether this thumbnail is flagged as a spoiler.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ThumbnailComponent.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### TextDisplay[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#textdisplay "Permalink to this headline")

_class_ discord.TextDisplay[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay "Permalink to this definition")

Represents a text display from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

New in version 2.6.

content[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay.content "Permalink to this definition")

The content that this display shows.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextDisplay.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### MediaGalleryComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#mediagallerycomponent "Permalink to this headline")

_class_ discord.MediaGalleryComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent "Permalink to this definition")

Represents a Media Gallery component from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

New in version 2.6.

items[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent.items "Permalink to this definition")

The items this gallery has.

Type

List[[`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem")]

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### FileComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#filecomponent "Permalink to this headline")

_class_ discord.FileComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent "Permalink to this definition")

Represents a File component from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type for create a file component is [`discord.ui.File`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File "discord.ui.File") not this one.

New in version 2.6.

media[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent.media "Permalink to this definition")

The unfurled attachment contents of the file.

Type

[`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")

spoiler[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent.spoiler "Permalink to this definition")

Whether this file is flagged as a spoiler.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent.name "Permalink to this definition")

The displayed file name, only available when received from the API.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

size[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent.size "Permalink to this definition")

The file size in MiB, only available when received from the API.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.FileComponent.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### SeparatorComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#separatorcomponent "Permalink to this headline")

_class_ discord.SeparatorComponent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent "Permalink to this definition")

Represents a Separator from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type for creating a separator is [`discord.ui.Separator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator "discord.ui.Separator") not this one.

New in version 2.6.

spacing[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent.spacing "Permalink to this definition")

The spacing size of the separator.

Type

[`SeparatorSpacing`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorSpacing "discord.SeparatorSpacing")

visible[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent.visible "Permalink to this definition")

Whether this separator is visible and shows a divider.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorComponent.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### Container[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#container "Permalink to this headline")

_class_ discord.Container[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container "Permalink to this definition")

Represents a Container from the Discord Bot UI Kit.

This inherits from [`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component").

Note

The user constructible and usable type for creating a container is [`discord.ui.Container`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container "discord.ui.Container") not this one.

New in version 2.6.

children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container.children "Permalink to this definition")

This container’s children.

Type

[`Component`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Component "discord.Component")

spoiler[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container.spoiler "Permalink to this definition")

Whether this container is flagged as a spoiler.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ accent_colour[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container.accent_colour "Permalink to this definition")

The container’s accent colour.

Type

Optional[[`Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour")]

_property_ accent_color[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container.accent_color "Permalink to this definition")

The container’s accent colour.

Type

Optional[[`Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour")]

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Container.type "Permalink to this definition")

The type of component.

Type

[`ComponentType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "discord.ComponentType")

### AppCommand[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appcommand "Permalink to this headline")

_class_ discord.app_commands.AppCommand[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "Permalink to this definition")

Represents an application command.

In common parlance this is referred to as a “Slash Command” or a “Context Menu Command”.

New in version 2.0.

x == y

Checks if two application commands are equal.

x != y

Checks if two application commands are not equal.

hash(x)

Returns the application command’s hash.

str(x)

Returns the application command’s name.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.id "Permalink to this definition")

The application command’s ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

application_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.application_id "Permalink to this definition")

The application command’s application’s ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.type "Permalink to this definition")

The application command’s type.

Type

[`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.name "Permalink to this definition")

The application command’s name.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.description "Permalink to this definition")

The application command’s description.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

name_localizations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.name_localizations "Permalink to this definition")

The localised names of the application command. Used for display purposes.

Type

Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

description_localizations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.description_localizations "Permalink to this definition")

The localised descriptions of the application command. Used for display purposes.

Type

Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

options[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.options "Permalink to this definition")

A list of options.

Type

List[Union[[`Argument`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument "discord.app_commands.Argument"), [`AppCommandGroup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup "discord.app_commands.AppCommandGroup")]]

default_member_permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.default_member_permissions "Permalink to this definition")

The default member permissions that can run this command.

Type

Optional[[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")]

dm_permission[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.dm_permission "Permalink to this definition")

A boolean that indicates whether this command can be run in direct messages.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

allowed_contexts[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.allowed_contexts "Permalink to this definition")

The contexts that this command is allowed to be used in. Overrides the `dm_permission` attribute.

New in version 2.4.

Type

Optional[[`AppCommandContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "discord.app_commands.AppCommandContext")]

allowed_installs[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.allowed_installs "Permalink to this definition")

The installation contexts that this command is allowed to be installed in.

New in version 2.4.

Type

Optional[[`AppInstallationType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType "discord.app_commands.AppInstallationType")]

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.guild_id "Permalink to this definition")

The ID of the guild this command is registered in. A value of `None` denotes that it is a global command.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

nsfw[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.nsfw "Permalink to this definition")

Whether the command is NSFW and should only work in NSFW channels.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ mention[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.mention "Permalink to this definition")

Returns a string that allows you to mention the given AppCommand.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.guild "Permalink to this definition")

Returns the guild this command is registered to if it exists.

Type

Optional[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

_await_ delete()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.delete "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Deletes the application command.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The application command was not found.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permission to delete this application command.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Deleting the application command failed.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The client does not have an application ID.
    

_await_ edit(_*_, _name=..._, _description=..._, _default_member_permissions=..._, _dm_permission=..._, _options=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.edit "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Edits the application command.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The new name for the application command.
    
*   **description** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The new description for the application command.
    
*   **default_member_permissions** (Optional[[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")]) – The new default permissions needed to use this application command. Pass value of `None` to remove any permission requirements.
    
*   **dm_permission** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates if the application command can be used in DMs.
    
*   **options** (List[Union[[`Argument`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument "discord.app_commands.Argument"), [`AppCommandGroup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup "discord.app_commands.AppCommandGroup")]]) – List of new options for this application command.
    

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The application command was not found.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permission to edit this application command.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Editing the application command failed.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The client does not have an application ID.
    

Returns

The newly edited application command.

Return type

[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand")

_await_ fetch_permissions(_guild_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand.fetch_permissions "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves this command’s permission in the guild.

Parameters

**guild** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The guild to retrieve the permissions from.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permission to fetch the application command’s permissions.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the application command’s permissions failed.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The client does not have an application ID.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The application command’s permissions could not be found. This can also indicate that the permissions are synced with the guild (i.e. they are unchanged from the default).
    

Returns

An object representing the application command’s permissions in the guild.

Return type

[`GuildAppCommandPermissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions "discord.app_commands.GuildAppCommandPermissions")

### AppCommandGroup[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appcommandgroup "Permalink to this headline")

_class_ discord.app_commands.AppCommandGroup[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup "Permalink to this definition")

Represents an application command subcommand.

New in version 2.0.

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.type "Permalink to this definition")

The type of subcommand.

Type

[`AppCommandOptionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "discord.AppCommandOptionType")

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.name "Permalink to this definition")

The name of the subcommand.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.description "Permalink to this definition")

The description of the subcommand.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

name_localizations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.name_localizations "Permalink to this definition")

The localised names of the subcommand. Used for display purposes.

Type

Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

description_localizations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.description_localizations "Permalink to this definition")

The localised descriptions of the subcommand. Used for display purposes.

Type

Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

options[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.options "Permalink to this definition")

A list of options.

Type

List[Union[[`Argument`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument "discord.app_commands.Argument"), [`AppCommandGroup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup "discord.app_commands.AppCommandGroup")]]

parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.parent "Permalink to this definition")

The parent application command.

Type

Union[[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand"), [`AppCommandGroup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup "discord.app_commands.AppCommandGroup")]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.qualified_name "Permalink to this definition")

Returns the fully qualified command name.

The qualified name includes the parent name as well. For example, in a command like `/foo bar` the qualified name is `foo bar`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ mention[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup.mention "Permalink to this definition")

Returns a string that allows you to mention the given AppCommandGroup.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

### AppCommandChannel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appcommandchannel "Permalink to this headline")

_class_ discord.app_commands.AppCommandChannel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel "Permalink to this definition")

Represents an application command partially resolved channel object.

New in version 2.0.

x == y

Checks if two channels are equal.

x != y

Checks if two channels are not equal.

hash(x)

Returns the channel’s hash.

str(x)

Returns the channel’s name.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.id "Permalink to this definition")

The ID of the channel.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.type "Permalink to this definition")

The type of channel.

Type

[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.name "Permalink to this definition")

The name of the channel.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.permissions "Permalink to this definition")

The resolved permissions of the user who invoked the application command in that channel.

Type

[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.guild_id "Permalink to this definition")

The guild ID this channel belongs to.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

category_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.category_id "Permalink to this definition")

The category channel ID this channel belongs to, if applicable.

New in version 2.6.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

topic[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.topic "Permalink to this definition")

The channel’s topic. `None` if it doesn’t exist.

New in version 2.6.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

position[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.position "Permalink to this definition")

The position in the channel list. This is a number that starts at 0. e.g. the top channel is position 0.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

last_message_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.last_message_id "Permalink to this definition")

The last message ID of the message sent to this channel. It may _not_ point to an existing or valid message.

New in version 2.6.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

slowmode_delay[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.slowmode_delay "Permalink to this definition")

The number of seconds a member must wait between sending messages in this channel. A value of `0` denotes that it is disabled. Bots and users with [`manage_channels`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_channels "discord.Permissions.manage_channels") or [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") bypass slowmode.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

nsfw[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.nsfw "Permalink to this definition")

If the channel is marked as “not safe for work” or “age restricted”.

New in version 2.6.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.guild "Permalink to this definition")

The channel’s guild, from cache, if found.

Type

Optional[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

_property_ flags[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.flags "Permalink to this definition")

The flags associated with this channel object.

New in version 2.6.

Type

[`ChannelFlags`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelFlags "discord.ChannelFlags")

is_nsfw()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.is_nsfw "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks if the channel is NSFW.

New in version 2.6.

is_news()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.is_news "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks if the channel is a news channel.

New in version 2.6.

resolve()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.resolve "Permalink to this definition")

Resolves the application command channel to the appropriate channel from cache if found.

Returns

The resolved guild channel or `None` if not found in cache.

Return type

Optional[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel")]

_await_ fetch()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.fetch "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Fetches the partial channel to a full [`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel").

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The channel was not found.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the permissions required to get a channel.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the channel failed.
    

Returns

The full channel.

Return type

[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel")

_property_ mention[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.mention "Permalink to this definition")

The string that allows you to mention the channel.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ jump_url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.jump_url "Permalink to this definition")

Returns a URL that allows the client to jump to the channel.

New in version 2.6.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ created_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandChannel.created_at "Permalink to this definition")

An aware timestamp of when this channel was created in UTC.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

### AppCommandThread[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appcommandthread "Permalink to this headline")

_class_ discord.app_commands.AppCommandThread[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread "Permalink to this definition")

Represents an application command partially resolved thread object.

New in version 2.0.

x == y

Checks if two thread are equal.

x != y

Checks if two thread are not equal.

hash(x)

Returns the thread’s hash.

str(x)

Returns the thread’s name.

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.id "Permalink to this definition")

The ID of the thread.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.type "Permalink to this definition")

The type of thread.

Type

[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.name "Permalink to this definition")

The name of the thread.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

parent_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.parent_id "Permalink to this definition")

The parent text channel ID this thread belongs to.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

owner_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.owner_id "Permalink to this definition")

The user’s ID that created this thread.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

last_message_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.last_message_id "Permalink to this definition")

The last message ID of the message sent to this thread. It may _not_ point to an existing or valid message.

New in version 2.6.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

slowmode_delay[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.slowmode_delay "Permalink to this definition")

The number of seconds a member must wait between sending messages in this thread. A value of `0` denotes that it is disabled. Bots and users with [`manage_channels`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_channels "discord.Permissions.manage_channels") or [`manage_messages`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_messages "discord.Permissions.manage_messages") bypass slowmode.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

message_count[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.message_count "Permalink to this definition")

An approximate number of messages in this thread.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

member_count[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.member_count "Permalink to this definition")

An approximate number of members in this thread. This caps at 50.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

total_message_sent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.total_message_sent "Permalink to this definition")

The total number of messages sent, including deleted messages.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.permissions "Permalink to this definition")

The resolved permissions of the user who invoked the application command in that thread.

Type

[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.guild_id "Permalink to this definition")

The guild ID this thread belongs to.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

archived[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.archived "Permalink to this definition")

Whether the thread is archived.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

locked[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.locked "Permalink to this definition")

Whether the thread is locked.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

invitable[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.invitable "Permalink to this definition")

Whether non-moderators can add other non-moderators to this thread. This is always `True` for public threads.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

archiver_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.archiver_id "Permalink to this definition")

The user’s ID that archived this thread.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

auto_archive_duration[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.auto_archive_duration "Permalink to this definition")

The duration in minutes until the thread is automatically hidden from the channel list. Usually a value of 60, 1440, 4320 and 10080.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

archive_timestamp[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.archive_timestamp "Permalink to this definition")

An aware timestamp of when the thread’s archived status was last updated in UTC.

Type

[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.guild "Permalink to this definition")

The channel’s guild, from cache, if found.

Type

Optional[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

_property_ applied_tags[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.applied_tags "Permalink to this definition")

A list of tags applied to this thread.

New in version 2.6.

Type

List[[`ForumTag`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ForumTag "discord.ForumTag")]

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.parent "Permalink to this definition")

The parent channel this thread belongs to.

Type

Optional[Union[[`ForumChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ForumChannel "discord.ForumChannel"), [`TextChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.TextChannel "discord.TextChannel")]]

_property_ flags[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.flags "Permalink to this definition")

The flags associated with this thread.

New in version 2.6.

Type

[`ChannelFlags`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelFlags "discord.ChannelFlags")

_property_ owner[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.owner "Permalink to this definition")

The member this thread belongs to.

New in version 2.6.

Type

Optional[[`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member")]

_property_ mention[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.mention "Permalink to this definition")

The string that allows you to mention the thread.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ jump_url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.jump_url "Permalink to this definition")

Returns a URL that allows the client to jump to the thread.

New in version 2.6.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ created_at[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.created_at "Permalink to this definition")

An aware timestamp of when the thread was created in UTC.

Note

This timestamp only exists for threads created after 9 January 2022, otherwise returns `None`.

resolve()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.resolve "Permalink to this definition")

Resolves the application command channel to the appropriate channel from cache if found.

Returns

The resolved guild channel or `None` if not found in cache.

Return type

Optional[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel")]

_await_ fetch()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandThread.fetch "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Fetches the partial channel to a full [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread").

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The thread was not found.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the permissions required to get a thread.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the thread failed.
    

Returns

The full thread.

Return type

[`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")

### AppCommandPermissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appcommandpermissions "Permalink to this headline")

_class_ discord.app_commands.AppCommandPermissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions "Permalink to this definition")

Represents the permissions for an application command.

New in version 2.0.

guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions.guild "Permalink to this definition")

The guild associated with this permission.

Type

[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions.id "Permalink to this definition")

The ID of the permission target, such as a role, channel, or guild. The special `guild_id - 1` sentinel is used to represent “all channels”.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

target[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions.target "Permalink to this definition")

The role, user, or channel associated with this permission. This could also be the [`AllChannels`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AllChannels "discord.app_commands.AllChannels") sentinel type. Falls back to [`Object`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Object "discord.Object") if the target could not be found in the cache.

Type

Any

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions.type "Permalink to this definition")

The type of permission.

Type

[`AppCommandPermissionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandPermissionType "discord.AppCommandPermissionType")

permission[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions.permission "Permalink to this definition")

The permission value. `True` for allow, `False` for deny.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### AppCommandContext[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appcommandcontext "Permalink to this headline")

_class_ discord.app_commands.AppCommandContext(_*_, _guild=None_, _dm_channel=None_, _private_channel=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "Permalink to this definition")

Wraps up the Discord [`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command") execution context.

New in version 2.4.

Parameters

*   **guild** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – Whether the context allows usage in a guild.
    
*   **dm_channel** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – Whether the context allows usage in a DM channel.
    
*   **private_channel** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – Whether the context allows usage in a DM or a GDM channel.
    

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext.guild "Permalink to this definition")

Whether the context allows usage in a guild.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ dm_channel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext.dm_channel "Permalink to this definition")

Whether the context allows usage in a DM channel.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ private_channel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext.private_channel "Permalink to this definition")

Whether the context allows usage in a DM or a GDM channel.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### AppInstallationType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#appinstallationtype "Permalink to this headline")

_class_ discord.app_commands.AppInstallationType(_*_, _guild=None_, _user=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType "Permalink to this definition")

Represents the installation location of an application command.

New in version 2.4.

Parameters

*   **guild** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – Whether the integration is a guild install.
    
*   **user** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – Whether the integration is a user install.
    

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType.guild "Permalink to this definition")

Whether the integration is a guild install.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType.user "Permalink to this definition")

Whether the integration is a user install.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### GuildAppCommandPermissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#guildappcommandpermissions "Permalink to this headline")

_class_ discord.app_commands.GuildAppCommandPermissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions "Permalink to this definition")

Represents the permissions for an application command in a guild.

New in version 2.0.

application_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions.application_id "Permalink to this definition")

The application ID.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions.command "Permalink to this definition")

The application command associated with the permissions.

Type

[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand")

id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions.id "Permalink to this definition")

ID of the command or the application ID. When this is the application ID instead of a command ID, the permissions apply to all commands that do not contain explicit overwrites.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions.guild_id "Permalink to this definition")

The guild ID associated with the permissions.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions.permissions "Permalink to this definition")

The permissions, this is a max of 100.

Type

List[[`AppCommandPermissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandPermissions "discord.app_commands.AppCommandPermissions")]

_property_ guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.GuildAppCommandPermissions.guild "Permalink to this definition")

The guild associated with the permissions.

Type

[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")

### Argument[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#argument "Permalink to this headline")

_class_ discord.app_commands.Argument[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument "Permalink to this definition")

Represents an application command argument.

New in version 2.0.

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.type "Permalink to this definition")

The type of argument.

Type

[`AppCommandOptionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "discord.AppCommandOptionType")

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.name "Permalink to this definition")

The name of the argument.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.description "Permalink to this definition")

The description of the argument.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

name_localizations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.name_localizations "Permalink to this definition")

The localised names of the argument. Used for display purposes.

Type

Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

description_localizations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.description_localizations "Permalink to this definition")

The localised descriptions of the argument. Used for display purposes.

Type

Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

required[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.required "Permalink to this definition")

Whether the argument is required.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

choices[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.choices "Permalink to this definition")

A list of choices for the command to choose from for this argument.

Type

List[[`Choice`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "discord.app_commands.Choice")]

parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.parent "Permalink to this definition")

The parent application command that has this argument.

Type

Union[[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand"), [`AppCommandGroup`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandGroup "discord.app_commands.AppCommandGroup")]

channel_types[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.channel_types "Permalink to this definition")

The channel types that are allowed for this parameter.

Type

List[[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")]

min_value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.min_value "Permalink to this definition")

The minimum supported value for this parameter.

Type

Optional[Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]]

max_value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.max_value "Permalink to this definition")

The maximum supported value for this parameter.

Type

Optional[Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]]

min_length[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.min_length "Permalink to this definition")

The minimum allowed length for this parameter.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

max_length[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.max_length "Permalink to this definition")

The maximum allowed length for this parameter.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

autocomplete[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Argument.autocomplete "Permalink to this definition")

Whether the argument has autocomplete.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### AllChannels[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#allchannels "Permalink to this headline")

_class_ discord.app_commands.AllChannels[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AllChannels "Permalink to this definition")

Represents all channels for application command permissions.

New in version 2.0.

guild[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AllChannels.guild "Permalink to this definition")

The guild the application command permission is for.

Type

[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AllChannels.id "Permalink to this definition")

The ID sentinel used to represent all channels. Equivalent to the guild’s ID minus 1.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

## Data Classes[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#data-classes "Permalink to this headline")

Similar to [Data Classes](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-data), these can be received and constructed by users.

### SelectOption[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#selectoption "Permalink to this headline")

_class_ discord.SelectOption(_*_, _label_, _value=..._, _description=None_, _emoji=None_, _default=False_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption "Permalink to this definition")

Represents a select menu’s option.

These can be created by users.

New in version 2.0.

Parameters

*   **label** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The label of the option. This is displayed to users. Can only be up to 100 characters.
    
*   **value** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The value of the option. This is not displayed to users. If not provided when constructed then it defaults to the label. Can only be up to 100 characters.
    
*   **description** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – An additional description of the option, if any. Can only be up to 100 characters.
    
*   **emoji** (Optional[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji")]]) – The emoji of the option, if available.
    
*   **default** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether this option is selected by default.
    

label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption.label "Permalink to this definition")

The label of the option. This is displayed to users.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption.value "Permalink to this definition")

The value of the option. This is not displayed to users. If not provided when constructed then it defaults to the label.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption.description "Permalink to this definition")

An additional description of the option, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

default[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption.default "Permalink to this definition")

Whether this option is selected by default.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ emoji[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption.emoji "Permalink to this definition")

The emoji of the option, if available.

Type

Optional[[`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji")]

### SelectDefaultValue[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#selectdefaultvalue "Permalink to this headline")

_class_ discord.SelectDefaultValue(_*_, _id_, _type_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "Permalink to this definition")

Represents a select menu’s default value.

These can be created by users.

New in version 2.4.

Parameters

*   **id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The id of a role, user, or channel.
    
*   **type** ([`SelectDefaultValueType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SelectDefaultValueType "discord.SelectDefaultValueType")) – The type of value that `id` represents.
    

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue.type "Permalink to this definition")

The type of value that `id` represents.

Type

[`SelectDefaultValueType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SelectDefaultValueType "discord.SelectDefaultValueType")

_classmethod_ from_channel(_channel_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue.from_channel "Permalink to this definition")

Creates a [`SelectDefaultValue`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "discord.SelectDefaultValue") with the type set to [`channel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SelectDefaultValueType.channel "discord.SelectDefaultValueType.channel").

Parameters

**channel** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The channel to create the default value for.

Returns

The default value created with the channel.

Return type

[`SelectDefaultValue`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "discord.SelectDefaultValue")

_classmethod_ from_role(_role_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue.from_role "Permalink to this definition")

Creates a [`SelectDefaultValue`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "discord.SelectDefaultValue") with the type set to [`role`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SelectDefaultValueType.role "discord.SelectDefaultValueType.role").

Parameters

**role** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The role to create the default value for.

Returns

The default value created with the role.

Return type

[`SelectDefaultValue`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "discord.SelectDefaultValue")

_classmethod_ from_user(_user_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue.from_user "Permalink to this definition")

Creates a [`SelectDefaultValue`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "discord.SelectDefaultValue") with the type set to [`user`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SelectDefaultValueType.user "discord.SelectDefaultValueType.user").

Parameters

**user** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The user to create the default value for.

Returns

The default value created with the user.

Return type

[`SelectDefaultValue`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectDefaultValue "discord.SelectDefaultValue")

### Choice[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#choice "Permalink to this headline")

_class_ discord.app_commands.Choice(_*_, _name_, _value_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "Permalink to this definition")

Represents an application command argument choice.

New in version 2.0.

x == y

Checks if two choices are equal.

x != y

Checks if two choices are not equal.

hash(x)

Returns the choice’s hash.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the choice. Used for display purposes. Can only be up to 100 characters.
    
*   **name_localizations** (Dict[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The localised names of the choice. Used for display purposes.
    
*   **value** (Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The value of the choice. If it’s a string, it can only be up to 100 characters long.
    

### UnfurledMediaItem[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#unfurledmediaitem "Permalink to this headline")

_class_ discord.UnfurledMediaItem(_url_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "Permalink to this definition")

Represents an unfurled media item.

New in version 2.6.

Parameters

**url** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The URL of this media item. This can be an arbitrary url or a reference to a local file uploaded as an attachment within the message, which can be accessed with the `attachment://<filename>` format.

url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.url "Permalink to this definition")

The URL of this media item.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

proxy_url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.proxy_url "Permalink to this definition")

The proxy URL. This is a cached version of the [`url`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.url "discord.UnfurledMediaItem.url") in the case of images. When the message is deleted, this URL might be valid for a few minutes or not valid at all.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

height[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.height "Permalink to this definition")

The media item’s height, in pixels. Only applicable to images and videos.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

width[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.width "Permalink to this definition")

The media item’s width, in pixels. Only applicable to images and videos.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

content_type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.content_type "Permalink to this definition")

The media item’s [media type](https://en.wikipedia.org/wiki/Media_type)

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

placeholder[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.placeholder "Permalink to this definition")

The media item’s placeholder.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

loading_state[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.loading_state "Permalink to this definition")

The loading state of this media item.

Type

Optional[[`MediaItemLoadingState`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MediaItemLoadingState "discord.MediaItemLoadingState")]

attachment_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.attachment_id "Permalink to this definition")

The attachment id this media item points to, only available if the url points to a local file uploaded within the component message.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ flags[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem.flags "Permalink to this definition")

This media item’s flags.

Type

[`AttachmentFlags`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AttachmentFlags "discord.AttachmentFlags")

### MediaGalleryItem[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#mediagalleryitem "Permalink to this headline")

_class_ discord.MediaGalleryItem(_media_, _*_, _description=..._, _spoiler=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "Permalink to this definition")

Represents a [`MediaGalleryComponent`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryComponent "discord.MediaGalleryComponent") media item.

New in version 2.6.

Parameters

*   **media** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`discord.File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File"), [`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")]) – The media item data. This can be a string representing a local file uploaded as an attachment in the message, which can be accessed using the `attachment://<filename>` format, or an arbitrary url.
    
*   **description** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The description to show within this item. Up to 256 characters. Defaults to `None`.
    
*   **spoiler** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether this item should be flagged as a spoiler.
    

_property_ media[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem.media "Permalink to this definition")

This item’s media data.

Type

[`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")

## Enumerations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#enumerations "Permalink to this headline")

_class_ discord.InteractionType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType "Permalink to this definition")

Specifies the type of [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction").

New in version 2.0.

ping[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.ping "Permalink to this definition")

Represents Discord pinging to see if the interaction response server is alive.

application_command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.application_command "Permalink to this definition")

Represents a slash command interaction.

component[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.component "Permalink to this definition")

Represents a component based interaction, i.e. using the Discord Bot UI Kit.

autocomplete[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.autocomplete "Permalink to this definition")

Represents an auto complete interaction.

modal_submit[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionType.modal_submit "Permalink to this definition")

Represents submission of a modal interaction.

_class_ discord.InteractionResponseType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType "Permalink to this definition")

Specifies the response type for the interaction.

New in version 2.0.

pong[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.pong "Permalink to this definition")

Pongs the interaction when given a ping.

See also [`InteractionResponse.pong()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.pong "discord.InteractionResponse.pong")

channel_message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.channel_message "Permalink to this definition")

Respond to the interaction with a message.

See also [`InteractionResponse.send_message()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_message "discord.InteractionResponse.send_message")

deferred_channel_message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.deferred_channel_message "Permalink to this definition")

Responds to the interaction with a message at a later time.

See also [`InteractionResponse.defer()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.defer "discord.InteractionResponse.defer")

deferred_message_update[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.deferred_message_update "Permalink to this definition")

Acknowledges the component interaction with a promise that the message will update later (though there is no need to actually update the message).

See also [`InteractionResponse.defer()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.defer "discord.InteractionResponse.defer")

message_update[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.message_update "Permalink to this definition")

Responds to the interaction by editing the message.

See also [`InteractionResponse.edit_message()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.edit_message "discord.InteractionResponse.edit_message")

autocomplete_result[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.autocomplete_result "Permalink to this definition")

Responds to the autocomplete interaction with suggested choices.

See also [`InteractionResponse.autocomplete()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.autocomplete "discord.InteractionResponse.autocomplete")

modal[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponseType.modal "Permalink to this definition")

Responds to the interaction with a modal.

See also [`InteractionResponse.send_modal()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_modal "discord.InteractionResponse.send_modal")

_class_ discord.ComponentType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType "Permalink to this definition")

Represents the component type of a component.

New in version 2.0.

action_row[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.action_row "Permalink to this definition")

Represents a component which holds different components in a row.

button[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.button "Permalink to this definition")

Represents a button component.

text_input[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.text_input "Permalink to this definition")

Represents a text box component.

select[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.select "Permalink to this definition")

Represents a select component.

string_select[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.string_select "Permalink to this definition")

An alias to [`select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.select "discord.ComponentType.select"). Represents a default select component.

user_select[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.user_select "Permalink to this definition")

Represents a user select component.

role_select[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.role_select "Permalink to this definition")

Represents a role select component.

mentionable_select[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.mentionable_select "Permalink to this definition")

Represents a select in which both users and roles can be selected.

channel_select[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.channel_select "Permalink to this definition")

Represents a channel select component.

section[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.section "Permalink to this definition")

Represents a component which holds different components in a section.

New in version 2.6.

text_display[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.text_display "Permalink to this definition")

Represents a text display component.

New in version 2.6.

thumbnail[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.thumbnail "Permalink to this definition")

Represents a thumbnail component.

New in version 2.6.

media_gallery[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.media_gallery "Permalink to this definition")

Represents a media gallery component.

New in version 2.6.

file[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.file "Permalink to this definition")

Represents a file component.

New in version 2.6.

separator[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.separator "Permalink to this definition")

Represents a separator component.

New in version 2.6.

container[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.container "Permalink to this definition")

Represents a component which holds different components in a container.

New in version 2.6.

label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ComponentType.label "Permalink to this definition")

Represents a label container component, usually in a modal.

New in version 2.6.

_class_ discord.ButtonStyle[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle "Permalink to this definition")

Represents the style of the button component.

New in version 2.0.

primary[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.primary "Permalink to this definition")

Represents a blurple button for the primary action.

secondary[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.secondary "Permalink to this definition")

Represents a grey button for the secondary action.

success[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.success "Permalink to this definition")

Represents a green button for a successful action.

danger[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.danger "Permalink to this definition")

Represents a red button for a dangerous action.

link[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.link "Permalink to this definition")

Represents a link button.

premium[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.premium "Permalink to this definition")

Represents a button denoting that buying a SKU is required to perform this action.

New in version 2.4.

blurple[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.blurple "Permalink to this definition")

An alias for [`primary`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.primary "discord.ButtonStyle.primary").

grey[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.grey "Permalink to this definition")

An alias for [`secondary`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.secondary "discord.ButtonStyle.secondary").

gray[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.gray "Permalink to this definition")

An alias for [`secondary`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.secondary "discord.ButtonStyle.secondary").

green[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.green "Permalink to this definition")

An alias for [`success`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.success "discord.ButtonStyle.success").

red[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.red "Permalink to this definition")

An alias for [`danger`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.danger "discord.ButtonStyle.danger").

url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.url "Permalink to this definition")

An alias for [`link`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.link "discord.ButtonStyle.link").

_class_ discord.TextStyle[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle "Permalink to this definition")

Represents the style of the text box component.

New in version 2.0.

short[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle.short "Permalink to this definition")

Represents a short text box.

paragraph[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle.paragraph "Permalink to this definition")

Represents a long form text box.

long[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle.long "Permalink to this definition")

An alias for [`paragraph`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle.paragraph "discord.TextStyle.paragraph").

_class_ discord.AppCommandOptionType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "Permalink to this definition")

The application command’s option type. This is usually the type of parameter an application command takes.

New in version 2.0.

subcommand[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.subcommand "Permalink to this definition")

A subcommand.

subcommand_group[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.subcommand_group "Permalink to this definition")

A subcommand group.

string[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.string "Permalink to this definition")

A string parameter.

integer[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.integer "Permalink to this definition")

A integer parameter.

boolean[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.boolean "Permalink to this definition")

A boolean parameter.

user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.user "Permalink to this definition")

A user parameter.

channel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.channel "Permalink to this definition")

A channel parameter.

role[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.role "Permalink to this definition")

A role parameter.

mentionable[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.mentionable "Permalink to this definition")

A mentionable parameter.

number[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.number "Permalink to this definition")

A number parameter.

attachment[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.attachment "Permalink to this definition")

An attachment parameter.

_class_ discord.AppCommandType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "Permalink to this definition")

The type of application command.

New in version 2.0.

chat_input[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType.chat_input "Permalink to this definition")

A slash command.

user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType.user "Permalink to this definition")

A user context menu command.

message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType.message "Permalink to this definition")

A message context menu command.

_class_ discord.AppCommandPermissionType[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandPermissionType "Permalink to this definition")

The application command’s permission type.

New in version 2.0.

role[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandPermissionType.role "Permalink to this definition")

The permission is for a role.

channel[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandPermissionType.channel "Permalink to this definition")

The permission is for one or all channels.

user[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandPermissionType.user "Permalink to this definition")

The permission is for a user.

_class_ discord.SeparatorSpacing[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorSpacing "Permalink to this definition")

The separator’s size type.

New in version 2.6.

small[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorSpacing.small "Permalink to this definition")

A small separator.

large[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorSpacing.large "Permalink to this definition")

A large separator.

## Bot UI Kit[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#bot-ui-kit "Permalink to this headline")

The library has helpers to aid in creating component-based UIs. These are all in the `discord.ui` package.

### View[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#view "Permalink to this headline")

_class_ discord.ui.View(_*_, _timeout=180.0_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "Permalink to this definition")

Represents a UI view.

This object must be inherited to create a UI within Discord.

New in version 2.0.

Parameters

**timeout** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – Timeout in seconds from last interaction with the UI before no longer accepting input. If `None` then there is no timeout.

_classmethod_ from_message(_message_, _/_, _*_, _timeout=180.0_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.from_message "Permalink to this definition")

Converts a message’s components into a [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") or [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView").

The [`Message.components`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.components "discord.Message.components") of a message are read-only and separate types from those in the `discord.ui` namespace. In order to modify and edit message components they must be converted into a [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") or [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") first.

If the message has any v2 components, then you must use [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") in order for them to be converted into their respective items. [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") does not support v2 components.

Parameters

*   **message** ([`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")) – The message with components to convert into a view.
    
*   **timeout** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The timeout of the converted view.
    

Returns

The converted view. This will always return one of [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") or [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView"), and not one of its subclasses.

Return type

Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]

add_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.add_item "Permalink to this definition")

Adds an item to the view.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to add to the view.

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of children has been exceeded, the row the item is trying to be added to is full or the item you tried to add is not allowed in this View.
    

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.remove_item "Permalink to this definition")

Removes an item from the view.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to remove from the view.

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.clear_items "Permalink to this definition")

Removes all items from the view.

This function returns the class instance to allow for fluent-style chaining.

_property_ children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.children "Permalink to this definition")

The list of children attached to this view.

Type

List[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

find_item(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.find_item "Permalink to this definition")

Gets an item with [`Item.id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "discord.ui.Item.id") set as `id`, or `None` if not found.

Warning

This is **not the same** as `custom_id`.

New in version 2.6.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the component.

Returns

The item found, or `None`.

Return type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within the view that checks whether the view should process item callbacks for the interaction.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

Note

If an exception occurs within the body then the check is considered a failure and [`on_error()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.on_error "discord.ui.View.on_error") is called.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the view children’s callbacks should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

is_dispatching()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.is_dispatching "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view has been added for dispatching purposes.

is_finished()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.is_finished "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view has finished interacting.

is_persistent()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.is_persistent "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view is set up as persistent.

A persistent view has all their components with a set `custom_id` and a [`timeout`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.timeout "discord.ui.View.timeout") set to `None`.

_await_ on_error(_interaction_, _error_, _item_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.on_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an item’s callback or [`interaction_check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.interaction_check "discord.ui.View.interaction_check") fails with an error.

The default implementation logs to the library logger.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that led to the failure.
    
*   **error** ([`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")) – The exception that was raised.
    
*   **item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item that failed the dispatch.
    

_await_ on_timeout()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.on_timeout "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when a view’s timeout elapses without being explicitly stopped.

stop()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.stop "Permalink to this definition")

Stops listening to interaction events from this view.

This operation cannot be undone.

_property_ timeout[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.timeout "Permalink to this definition")

The timeout in seconds from last interaction with the UI before no longer accepting input. If `None` then there is no timeout.

Type

Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]

_property_ total_children_count[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.total_children_count "Permalink to this definition")

The total number of children in this view, including those from nested items.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_await_ wait()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.wait "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Waits until the view has finished interacting.

A view is considered finished when [`stop()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.stop "discord.ui.View.stop") is called or it times out.

Returns

If `True`, then the view timed out. If `False` then the view finished normally.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_for ... in_ walk_children()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View.walk_children "Permalink to this definition")

An iterator that recursively walks through all the children of this view and its children, if applicable.

New in version 2.6.

Yields

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") – An item in the view.

### LayoutView[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#layoutview "Permalink to this headline")

_class_ discord.ui.LayoutView(_*_, _timeout=180.0_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "Permalink to this definition")

Represents a layout view for components.

This object must be inherited to create a UI within Discord.

This differs from a [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") in that it supports all component types and uses what Discord refers to as “v2 components”.

You can find usage examples in the [repository](https://github.com/Rapptz/discord.py/tree/v2.6.3/examples)

New in version 2.6.

Parameters

**timeout** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – Timeout in seconds from last interaction with the UI before no longer accepting input. If `None` then there is no timeout.

_classmethod_ from_message(_message_, _/_, _*_, _timeout=180.0_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.from_message "Permalink to this definition")

Converts a message’s components into a [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") or [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView").

The [`Message.components`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.components "discord.Message.components") of a message are read-only and separate types from those in the `discord.ui` namespace. In order to modify and edit message components they must be converted into a [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") or [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") first.

If the message has any v2 components, then you must use [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") in order for them to be converted into their respective items. [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") does not support v2 components.

Parameters

*   **message** ([`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")) – The message with components to convert into a view.
    
*   **timeout** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The timeout of the converted view.
    

Returns

The converted view. This will always return one of [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") or [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView"), and not one of its subclasses.

Return type

Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]

add_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.add_item "Permalink to this definition")

Adds an item to the view.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to add to the view.

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of children has been exceeded, the row the item is trying to be added to is full or the item you tried to add is not allowed in this View.
    

content_length()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.content_length "Permalink to this definition")

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"): Returns the total length of all text content in the view’s items.

A view is allowed to have a maximum of 4000 display characters across all its items.

_property_ children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.children "Permalink to this definition")

The list of children attached to this view.

Type

List[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.clear_items "Permalink to this definition")

Removes all items from the view.

This function returns the class instance to allow for fluent-style chaining.

find_item(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.find_item "Permalink to this definition")

Gets an item with [`Item.id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "discord.ui.Item.id") set as `id`, or `None` if not found.

Warning

This is **not the same** as `custom_id`.

New in version 2.6.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the component.

Returns

The item found, or `None`.

Return type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within the view that checks whether the view should process item callbacks for the interaction.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

Note

If an exception occurs within the body then the check is considered a failure and [`on_error()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.on_error "discord.ui.LayoutView.on_error") is called.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the view children’s callbacks should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

is_dispatching()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.is_dispatching "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view has been added for dispatching purposes.

is_finished()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.is_finished "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view has finished interacting.

is_persistent()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.is_persistent "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view is set up as persistent.

A persistent view has all their components with a set `custom_id` and a [`timeout`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.timeout "discord.ui.LayoutView.timeout") set to `None`.

_await_ on_error(_interaction_, _error_, _item_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.on_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an item’s callback or [`interaction_check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.interaction_check "discord.ui.LayoutView.interaction_check") fails with an error.

The default implementation logs to the library logger.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that led to the failure.
    
*   **error** ([`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")) – The exception that was raised.
    
*   **item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item that failed the dispatch.
    

_await_ on_timeout()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.on_timeout "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when a view’s timeout elapses without being explicitly stopped.

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.remove_item "Permalink to this definition")

Removes an item from the view.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to remove from the view.

stop()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.stop "Permalink to this definition")

Stops listening to interaction events from this view.

This operation cannot be undone.

_property_ timeout[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.timeout "Permalink to this definition")

The timeout in seconds from last interaction with the UI before no longer accepting input. If `None` then there is no timeout.

Type

Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]

_property_ total_children_count[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.total_children_count "Permalink to this definition")

The total number of children in this view, including those from nested items.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_await_ wait()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.wait "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Waits until the view has finished interacting.

A view is considered finished when [`stop()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.stop "discord.ui.LayoutView.stop") is called or it times out.

Returns

If `True`, then the view timed out. If `False` then the view finished normally.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_for ... in_ walk_children()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView.walk_children "Permalink to this definition")

An iterator that recursively walks through all the children of this view and its children, if applicable.

New in version 2.6.

Yields

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") – An item in the view.

### Modal[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#modal "Permalink to this headline")

_class_ discord.ui.Modal(_*_, _title=..._, _timeout=None_, _custom_id=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal "Permalink to this definition")

Represents a UI modal.

This object must be inherited to create a modal popup window within discord.

New in version 2.0.

Examples

content_copy

```
import discord
from discord import ui

class Questionnaire(ui.Modal, title='Questionnaire Response'):
    name = ui.TextInput(label='Name')
    answer = ui.TextInput(label='Answer', style=discord.TextStyle.paragraph)

    async def on_submit(self, interaction: discord.Interaction):
        await interaction.response.send_message(f'Thanks for your response, {self.name}!', ephemeral=True)
```

Parameters

*   **title** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The title of the modal. Can only be up to 45 characters.
    
*   **timeout** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – Timeout in seconds from last interaction with the UI before no longer accepting input. If `None` then there is no timeout.
    
*   **custom_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The ID of the modal that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
    

title[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.title "Permalink to this definition")

The title of the modal.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

custom_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.custom_id "Permalink to this definition")

The ID of the modal that gets received during an interaction.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_await_ on_submit(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.on_submit "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Called when the modal is submitted.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that submitted this modal.

_await_ on_error(_interaction_, _error_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.on_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when [`on_submit()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.on_submit "discord.ui.Modal.on_submit") fails with an error.

The default implementation logs to the library logger.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that led to the failure.
    
*   **error** ([`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")) – The exception that was raised.
    

add_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.add_item "Permalink to this definition")

Adds an item to the view.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to add to the view.

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of children has been exceeded, the row the item is trying to be added to is full or the item you tried to add is not allowed in this View.
    

_property_ children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.children "Permalink to this definition")

The list of children attached to this view.

Type

List[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.clear_items "Permalink to this definition")

Removes all items from the view.

This function returns the class instance to allow for fluent-style chaining.

find_item(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.find_item "Permalink to this definition")

Gets an item with [`Item.id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "discord.ui.Item.id") set as `id`, or `None` if not found.

Warning

This is **not the same** as `custom_id`.

New in version 2.6.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the component.

Returns

The item found, or `None`.

Return type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within the view that checks whether the view should process item callbacks for the interaction.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

Note

If an exception occurs within the body then the check is considered a failure and [`on_error()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.on_error "discord.ui.Modal.on_error") is called.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the view children’s callbacks should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

is_dispatching()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.is_dispatching "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view has been added for dispatching purposes.

is_finished()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.is_finished "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view has finished interacting.

is_persistent()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.is_persistent "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the view is set up as persistent.

A persistent view has all their components with a set `custom_id` and a [`timeout`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.timeout "discord.ui.Modal.timeout") set to `None`.

_await_ on_timeout()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.on_timeout "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when a view’s timeout elapses without being explicitly stopped.

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.remove_item "Permalink to this definition")

Removes an item from the view.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to remove from the view.

stop()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.stop "Permalink to this definition")

Stops listening to interaction events from this view.

This operation cannot be undone.

_property_ timeout[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.timeout "Permalink to this definition")

The timeout in seconds from last interaction with the UI before no longer accepting input. If `None` then there is no timeout.

Type

Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]

_property_ total_children_count[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.total_children_count "Permalink to this definition")

The total number of children in this view, including those from nested items.

New in version 2.6.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_await_ wait()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.wait "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Waits until the view has finished interacting.

A view is considered finished when [`stop()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.stop "discord.ui.Modal.stop") is called or it times out.

Returns

If `True`, then the view timed out. If `False` then the view finished normally.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_for ... in_ walk_children()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Modal.walk_children "Permalink to this definition")

An iterator that recursively walks through all the children of this view and its children, if applicable.

New in version 2.6.

Yields

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") – An item in the view.

### Item[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#item "Permalink to this headline")

_class_ discord.ui.Item[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "Permalink to this definition")

Represents the base UI item that all UI components inherit from.

The current UI items supported are:

*   [`discord.ui.Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button")
    
*   [`discord.ui.Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select")
    
*   [`discord.ui.TextInput`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput "discord.ui.TextInput")
    
*   [`discord.ui.ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "discord.ui.ActionRow")
    
*   [`discord.ui.Container`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container "discord.ui.Container")
    
*   [`discord.ui.File`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File "discord.ui.File")
    
*   [`discord.ui.MediaGallery`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery "discord.ui.MediaGallery")
    
*   [`discord.ui.Section`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section "discord.ui.Section")
    
*   [`discord.ui.Separator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator "discord.ui.Separator")
    
*   [`discord.ui.TextDisplay`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay "discord.ui.TextDisplay")
    
*   [`discord.ui.Thumbnail`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail "discord.ui.Thumbnail")
    
*   [`discord.ui.Label`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label "discord.ui.Label")
    

New in version 2.0.

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_await_ callback(_interaction_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.callback "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The callback associated with this UI item.

This can be overridden by subclasses.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that triggered this UI item.

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within this item that checks whether the callback should be processed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

New in version 2.4.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the callback should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### DynamicItem[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#dynamicitem "Permalink to this headline")

_class_ discord.ui.DynamicItem(_item_, _*_, _row=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "Permalink to this definition")

Represents an item with a dynamic `custom_id` that can be used to store state within that `custom_id`.

The `custom_id` parsing is done using the `re` module by passing a `template` parameter to the class parameter list.

This item is generated every time the component is dispatched. This means that any variable that holds an instance of this class will eventually be out of date and should not be used long term. Their only purpose is to act as a “template” for the actual dispatched item.

When this item is generated, [`view`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.view "discord.ui.DynamicItem.view") is set to a regular [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") instance, but to a [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") if the component was sent with one, this is obtained from the original message given from the interaction. This means that custom view subclasses cannot be accessed from this item.

New in version 2.4.

Parameters

*   **item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to wrap with dynamic custom ID parsing.
    
*   **template** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), `re.Pattern`]) – The template to use for parsing the `custom_id`. This can be a string or a compiled regular expression. This must be passed as a keyword argument to the class creation.
    
*   **row** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The relative row this button belongs to. A Discord component can only have 5 rows. By default, items are arranged automatically into those 5 rows. If you’d like to control the relative positioning of the row then passing an index is advised. For example, row=1 will show up before row=2. Defaults to `None`, which is automatic ordering. The row number must be between 0 and 4 (i.e. zero indexed).
    

item[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.item "Permalink to this definition")

The item that is wrapped with dynamic custom ID parsing.

Type

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")

_property_ template[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.template "Permalink to this definition")

The compiled regular expression that is used to parse the `custom_id`.

Type

`re.Pattern`

_property_ custom_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.custom_id "Permalink to this definition")

The ID of the dynamic item that gets received during an interaction.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

_classmethod await_ from_custom_id(_interaction_, _item_, _match_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.from_custom_id "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A classmethod that is called when the `custom_id` of a component matches the `template` of the class. This is called when the component is dispatched.

It must return a new instance of the [`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem").

Subclasses _must_ implement this method.

Exceptions raised in this method are logged and ignored.

Warning

This method is called before the callback is dispatched, therefore it means that it is subject to the same timing restrictions as the callback. Ergo, you must reply to an interaction within 3 seconds of it being dispatched.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that the component belongs to.
    
*   **item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The base item that is being dispatched.
    
*   **match** (`re.Match`) – The match object that was created from the `template` matching the `custom_id`.
    

Returns

The new instance of the [`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem") with information from the `match` object.

Return type

[`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem")

_await_ callback(_interaction_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.callback "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The callback associated with this UI item.

This can be overridden by subclasses.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that triggered this UI item.

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within this item that checks whether the callback should be processed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

New in version 2.4.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the callback should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### Button[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#id1 "Permalink to this headline")

_class_ discord.ui.Button(_*_, _style=<ButtonStyle.secondary: 2>_, _label=None_, _disabled=False_, _custom_id=None_, _url=None_, _emoji=None_, _row=None_, _sku_id=None_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "Permalink to this definition")

Represents a UI button.

New in version 2.0.

Parameters

*   **style** ([`discord.ButtonStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle "discord.ButtonStyle")) – The style of the button.
    
*   **custom_id** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The ID of the button that gets received during an interaction. If this button is for a URL, it does not have a custom ID. Can only be up to 100 characters.
    
*   **url** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The URL this button sends you to.
    
*   **disabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the button is disabled or not.
    
*   **label** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The label of the button, if any. Can only be up to 80 characters.
    
*   **emoji** (Optional[Union[[`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji"), [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]]) – The emoji of the button, if available.
    
*   **row** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The relative row this button belongs to. A Discord component can only have 5 rows. By default, items are arranged automatically into those 5 rows. If you’d like to control the relative positioning of the row then passing an index is advised. For example, row=1 will show up before row=2. Defaults to `None`, which is automatic ordering. The row number must be between 0 and 4 (i.e. zero indexed).
    
    Note
    
    This parameter is ignored when used in a [`ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "discord.ui.ActionRow") or v2 component.
    
*   **sku_id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The SKU ID this button sends you to. Can’t be combined with `url`, `label`, `emoji` nor `custom_id`.
    
    New in version 2.4.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The ID of this component. This must be unique across the view.
    
    New in version 2.6.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.id "Permalink to this definition")

The ID of this button.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ style[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.style "Permalink to this definition")

The style of the button.

Type

[`discord.ButtonStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle "discord.ButtonStyle")

_property_ custom_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.custom_id "Permalink to this definition")

The ID of the button that gets received during an interaction.

If this button is for a URL, it does not have a custom ID.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.url "Permalink to this definition")

The URL this button sends you to.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ disabled[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.disabled "Permalink to this definition")

Whether the button is disabled or not.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.label "Permalink to this definition")

The label of the button, if available.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ emoji[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.emoji "Permalink to this definition")

The emoji of the button, if available.

Type

Optional[[`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji")]

_property_ sku_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.sku_id "Permalink to this definition")

The SKU ID this button sends you to.

New in version 2.4.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_await_ callback(_interaction_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.callback "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The callback associated with this UI item.

This can be overridden by subclasses.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that triggered this UI item.

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within this item that checks whether the callback should be processed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

New in version 2.4.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the callback should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

@discord.ui.button(_*_, _label=None_, _custom_id=None_, _disabled=False_, _style=<ButtonStyle.secondary: 2>_, _emoji=None_, _row=None_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.button "Permalink to this definition")

A decorator that attaches a button to a component.

The function being decorated should have three parameters, `self` representing the [`discord.ui.View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), the [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") you receive and the [`discord.ui.Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button") being pressed.

Note

Buttons with a URL or an SKU cannot be created with this function. Consider creating a [`Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button") manually instead. This is because these buttons cannot have a callback associated with them since Discord does not do any processing with them.

Parameters

*   **label** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The label of the button, if any. Can only be up to 80 characters.
    
*   **custom_id** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The ID of the button that gets received during an interaction. It is recommended not to set this parameter to prevent conflicts. Can only be up to 100 characters.
    
*   **style** ([`ButtonStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle "discord.ButtonStyle")) – The style of the button. Defaults to [`ButtonStyle.grey`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.grey "discord.ButtonStyle.grey").
    
*   **disabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the button is disabled or not. Defaults to `False`.
    
*   **emoji** (Optional[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji")]]) – The emoji of the button. This can be in string form or a [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji") or a full [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji").
    
*   **row** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The relative row this button belongs to. A Discord component can only have 5 rows. By default, items are arranged automatically into those 5 rows. If you’d like to control the relative positioning of the row then passing an index is advised. For example, row=1 will show up before row=2. Defaults to `None`, which is automatic ordering. The row number must be between 0 and 4 (i.e. zero indexed).
    
    Note
    
    This parameter is ignored when used in a [`ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "discord.ui.ActionRow") or v2 component.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The ID of this component. This must be unique across the view.
    
    New in version 2.6.
    

### TextInput[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#id3 "Permalink to this headline")

_class_ discord.ui.TextInput(_*_, _label=None_, _style=<TextStyle.short: 1>_, _custom_id=..._, _placeholder=None_, _default=None_, _required=True_, _min_length=None_, _max_length=None_, _row=None_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput "Permalink to this definition")

Represents a UI text input.

str(x)

Returns the value of the text input or an empty string if the value is `None`.

New in version 2.0.

Parameters

*   **label** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) –
    
    The label to display above the text input. Can only be up to 45 characters.
    
    Deprecated since version 2.6: This parameter is deprecated, use [`discord.ui.Label`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label "discord.ui.Label") instead.
    
    Changed in version 2.6: This parameter is now optional and defaults to `None`.
    
*   **custom_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The ID of the text input that gets received during an interaction. If not given then one is generated for you. Can only be up to 100 characters.
    
*   **style** ([`discord.TextStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle "discord.TextStyle")) – The style of the text input.
    
*   **placeholder** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The placeholder text to display when the text input is empty. Can only be up to 100 characters.
    
*   **default** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The default value of the text input. Can only be up to 4000 characters.
    
*   **required** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the text input is required.
    
*   **min_length** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The minimum length of the text input. Must be between 0 and 4000.
    
*   **max_length** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The maximum length of the text input. Must be between 1 and 4000.
    
*   **row** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The relative row this text input belongs to. A Discord component can only have 5 rows. By default, items are arranged automatically into those 5 rows. If you’d like to control the relative positioning of the row then passing an index is advised. For example, row=1 will show up before row=2. Defaults to `None`, which is automatic ordering. The row number must be between 0 and 4 (i.e. zero indexed).
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The ID of the component. This must be unique across the view.
    
    New in version 2.6.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ custom_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.custom_id "Permalink to this definition")

The ID of the text input that gets received during an interaction.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.value "Permalink to this definition")

The value of the text input.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.label "Permalink to this definition")

The label of the text input.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ placeholder[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.placeholder "Permalink to this definition")

The placeholder text to display when the text input is empty.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ required[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.required "Permalink to this definition")

Whether the text input is required.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ min_length[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.min_length "Permalink to this definition")

The minimum length of the text input.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_property_ max_length[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.max_length "Permalink to this definition")

The maximum length of the text input.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_property_ style[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.style "Permalink to this definition")

The style of the text input.

Type

[`discord.TextStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.TextStyle "discord.TextStyle")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

_property_ default[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput.default "Permalink to this definition")

The default value of the text input.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

### Container[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#id4 "Permalink to this headline")

_class_ discord.ui.Container(_*children_, _accent_colour=None_, _accent_color=None_, _spoiler=False_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container "Permalink to this definition")

Represents a UI container.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") and can contain [`ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "discord.ui.ActionRow")s, [`TextDisplay`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay "discord.ui.TextDisplay")s, [`Section`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section "discord.ui.Section")s, [`MediaGallery`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery "discord.ui.MediaGallery")s, [`File`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File "discord.ui.File")s, and [`Separator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator "discord.ui.Separator")s in it.

This can be inherited.

New in version 2.6.

Examples

content_copy

```
import discord
from discord import ui

# you can subclass it and add components as you would add them
# in a LayoutView
class MyContainer(ui.Container):
    action_row = ui.ActionRow()

 @action_row.button(label='A button in a container!')
    async def a_button(self, interaction: discord.Interaction, button: discord.ui.Button):
        await interaction.response.send_message('You clicked a button!')

# or use it directly on LayoutView
class MyView(ui.LayoutView):
    container = ui.Container(ui.TextDisplay('I am a text display on a container!'))
    # or you can use your subclass:
    # container = MyContainer()
```

Parameters

*   ***children** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The initial children of this container.
    
*   **accent_colour** (Optional[Union[[`Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]) – The colour of the container. Defaults to `None`.
    
*   **accent_color** (Optional[Union[[`Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]) – The color of the container. Defaults to `None`.
    
*   **spoiler** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to flag this container as a spoiler. Defaults to `False`.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.children "Permalink to this definition")

The children of this container.

Type

List[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ accent_colour[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.accent_colour "Permalink to this definition")

The colour of the container, or `None`.

Type

Optional[Union[[`discord.Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]

_property_ accent_color[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.accent_color "Permalink to this definition")

The colour of the container, or `None`.

Type

Optional[Union[[`discord.Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]

_for ... in_ walk_children()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.walk_children "Permalink to this definition")

An iterator that recursively walks through all the children of this container and its children, if applicable.

Yields

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") – An item in the container.

content_length()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.content_length "Permalink to this definition")

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"): Returns the total length of all text content in this container.

add_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.add_item "Permalink to this definition")

Adds an item to this container.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to append.

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of children has been exceeded (40) for the entire view.
    

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.remove_item "Permalink to this definition")

Removes an item from this container.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to remove from the container.

find_item(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.find_item "Permalink to this definition")

Gets an item with [`Item.id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "discord.ui.Item.id") set as `id`, or `None` if not found.

Warning

This is **not the same** as `custom_id`.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the component.

Returns

The item found, or `None`.

Return type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within this item that checks whether the callback should be processed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

New in version 2.4.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the callback should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Container.clear_items "Permalink to this definition")

Removes all the items from the container.

This function returns the class instance to allow for fluent-style chaining.

### File[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#file "Permalink to this headline")

_class_ discord.ui.File(_media_, _*_, _spoiler=..._, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File "Permalink to this definition")

Represents a UI file component.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView").

New in version 2.6.

Example

content_copy

```
import discord
from discord import ui

class MyView(ui.LayoutView):
    file = ui.File('attachment://file.txt')
    # attachment://file.txt points to an attachment uploaded alongside this view
```

Parameters

*   **media** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem"), [`discord.File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")]) – This file’s media. If this is a string it must point to a local file uploaded within the parent view of this item, and must meet the `attachment://<filename>` format.
    
*   **spoiler** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to flag this file as a spoiler. Defaults to `False`.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ media[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File.media "Permalink to this definition")

Returns this file media.

Type

[`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")

_property_ url[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File.url "Permalink to this definition")

Returns this file’s url.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

_property_ spoiler[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.File.spoiler "Permalink to this definition")

Returns whether this file should be flagged as a spoiler.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### Label[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#label "Permalink to this headline")

_class_ discord.ui.Label(_*_, _text_, _component_, _description=None_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label "Permalink to this definition")

Represents a UI label within a modal.

New in version 2.6.

Parameters

*   **text** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The text to display above the input field. Can only be up to 45 characters.
    
*   **description** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The description text to display right below the label text. Can only be up to 100 characters.
    
*   **component** (Union[[`discord.ui.TextInput`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput "discord.ui.TextInput"), [`discord.ui.Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select")]) – The component to display below the label.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of the component. This must be unique across the view.
    

text[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label.text "Permalink to this definition")

The text to display above the input field. Can only be up to 45 characters.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label.description "Permalink to this definition")

The description text to display right below the label text. Can only be up to 100 characters.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

component[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label.component "Permalink to this definition")

The component to display below the label. Currently only supports [`TextInput`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextInput "discord.ui.TextInput") and [`Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select").

Type

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Label.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

### MediaGallery[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#mediagallery "Permalink to this headline")

_class_ discord.ui.MediaGallery(_*items_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery "Permalink to this definition")

Represents a UI media gallery.

Can contain up to 10 [`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem")s.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView").

New in version 2.6.

Parameters

*   ***items** ([`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem")) – The initial items of this gallery.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ items[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.items "Permalink to this definition")

Returns a read-only list of this gallery’s items.

Type

List[[`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem")]

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

add_item(_*_, _media_, _description=..._, _spoiler=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.add_item "Permalink to this definition")

Adds an item to this gallery.

This function returns the class instance to allow for fluent-style chaining.

Parameters

*   **media** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`discord.File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File"), [`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")]) – The media item data. This can be a string representing a local file uploaded as an attachment in the message, which can be accessed using the `attachment://<filename>` format, or an arbitrary url.
    
*   **description** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The description to show within this item. Up to 256 characters. Defaults to `None`.
    
*   **spoiler** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether this item should be flagged as a spoiler. Defaults to `False`.
    

Raises

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of items has been exceeded (10).

append_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.append_item "Permalink to this definition")

Appends an item to this gallery.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem")) – The item to add to the gallery.

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – A [`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of items has been exceeded (10).
    

insert_item_at(_index_, _*_, _media_, _description=..._, _spoiler=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.insert_item_at "Permalink to this definition")

Inserts an item before a specified index to the media gallery.

This function returns the class instance to allow for fluent-style chaining.

Parameters

*   **index** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The index of where to insert the field.
    
*   **media** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`discord.File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File"), [`UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")]) – The media item data. This can be a string representing a local file uploaded as an attachment in the message, which can be accessed using the `attachment://<filename>` format, or an arbitrary url.
    
*   **description** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The description to show within this item. Up to 256 characters. Defaults to `None`.
    
*   **spoiler** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether this item should be flagged as a spoiler. Defaults to `False`.
    

Raises

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of items has been exceeded (10).

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.remove_item "Permalink to this definition")

Removes an item from the gallery.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`MediaGalleryItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.MediaGalleryItem "discord.MediaGalleryItem")) – The item to remove from the gallery.

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.clear_items "Permalink to this definition")

Removes all items from the gallery.

This function returns the class instance to allow for fluent-style chaining.

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MediaGallery.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

### Section[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#section "Permalink to this headline")

_class_ discord.ui.Section(_*children_, _accessory_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section "Permalink to this definition")

Represents a UI section.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView").

New in version 2.6.

Parameters

*   ***children** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`TextDisplay`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay "discord.ui.TextDisplay")]) – The text displays of this section. Up to 3.
    
*   **accessory** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The section accessory.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.children "Permalink to this definition")

The list of children attached to this section.

Type

List[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ accessory[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.accessory "Permalink to this definition")

The section’s accessory.

Type

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")

_for ... in_ walk_children()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.walk_children "Permalink to this definition")

An iterator that recursively walks through all the children of this section and its children, if applicable. This includes the accessory.

Yields

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") – An item in this section.

content_length()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.content_length "Permalink to this definition")

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"): Returns the total length of all text content in this section.

add_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.add_item "Permalink to this definition")

Adds an item to this section.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]) – The item to append, if it is a string it automatically wrapped around [`TextDisplay`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay "discord.ui.TextDisplay").

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") or [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of children has been exceeded (3) or (40) for the entire view.
    

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.remove_item "Permalink to this definition")

Removes an item from this section.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to remove from the section.

find_item(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.find_item "Permalink to this definition")

Gets an item with [`Item.id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "discord.ui.Item.id") set as `id`, or `None` if not found.

Warning

This is **not the same** as `custom_id`.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the component.

Returns

The item found, or `None`.

Return type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.clear_items "Permalink to this definition")

Removes all the items from the section.

This function returns the class instance to allow for fluent-style chaining.

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within this item that checks whether the callback should be processed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

New in version 2.4.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the callback should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

### Separator[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#separator "Permalink to this headline")

_class_ discord.ui.Separator(_*_, _visible=True_, _spacing=<SeparatorSpacing.small: 1>_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator "Permalink to this definition")

Represents a UI separator.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView").

New in version 2.6.

Parameters

*   **visible** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether this separator is visible. On the client side this is whether a divider line should be shown or not.
    
*   **spacing** ([`SeparatorSpacing`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorSpacing "discord.SeparatorSpacing")) – The spacing of this separator.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ visible[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator.visible "Permalink to this definition")

Whether this separator is visible.

On the client side this is whether a divider line should be shown or not.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ spacing[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator.spacing "Permalink to this definition")

The spacing of this separator.

Type

[`SeparatorSpacing`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SeparatorSpacing "discord.SeparatorSpacing")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Separator.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

### TextDisplay[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#id5 "Permalink to this headline")

_class_ discord.ui.TextDisplay(_content_, _*_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay "Permalink to this definition")

Represents a UI text display.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") or [`Section`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section "discord.ui.Section").

New in version 2.6.

Parameters

*   **content** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The content of this text display. Up to 4000 characters.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.TextDisplay.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

### Thumbnail[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#thumbnail "Permalink to this headline")

_class_ discord.ui.Thumbnail(_media_, _*_, _description=..._, _spoiler=..._, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail "Permalink to this definition")

Represents a UI Thumbnail. This currently can only be used as a [`Section`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Section "discord.ui.Section")’s accessory.

New in version 2.6.

Parameters

*   **media** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`discord.File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File"), [`discord.UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")]) – The media of the thumbnail. This can be a URL or a reference to an attachment that matches the `attachment://filename.extension` structure.
    
*   **description** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The description of this thumbnail. Up to 256 characters. Defaults to `None`.
    
*   **spoiler** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to flag this thumbnail as a spoiler. Defaults to `False`.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ media[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail.media "Permalink to this definition")

This thumbnail unfurled media data.

Type

[`discord.UnfurledMediaItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.UnfurledMediaItem "discord.UnfurledMediaItem")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Thumbnail.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

### ActionRow[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#id6 "Permalink to this headline")

_class_ discord.ui.ActionRow(_*children_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "Permalink to this definition")

Represents a UI action row.

This is a top-level layout component that can only be used on [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView") and can contain [`Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button")s and [`Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select")s in it.

Action rows can only have 5 children. This can be inherited.

New in version 2.6.

Examples

content_copy

```
import discord
from discord import ui

# you can subclass it and add components with the decorators
class MyActionRow(ui.ActionRow):
 @ui.button(label='Click Me!')
    async def click_me(self, interaction: discord.Interaction, button: discord.ui.Button):
        await interaction.response.send_message('You clicked me!')

# or use it directly on LayoutView
class MyView(ui.LayoutView):
    row = ui.ActionRow()
    # or you can use your subclass:
    # row = MyActionRow()

    # you can add items with row.button and row.select
 @row.button(label='A button!')
    async def row_button(self, interaction: discord.Interaction, button: discord.ui.Button):
        await interaction.response.send_message('You clicked a button!')
```

Parameters

*   ***children** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The initial children of this action row.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The ID of this component. This must be unique across the view.
    

_property_ id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.id "Permalink to this definition")

The ID of this component.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ children[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.children "Permalink to this definition")

The list of children attached to this action row.

Type

List[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_for ... in_ walk_children()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.walk_children "Permalink to this definition")

An iterator that recursively walks through all the children of this action row and its children, if applicable.

Yields

[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") – An item in the action row.

content_length()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.content_length "Permalink to this definition")

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"): Returns the total length of all text content in this action row.

add_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.add_item "Permalink to this definition")

Adds an item to this action row.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to add to the action row.

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An [`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item") was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Maximum number of children has been exceeded (5) or (40) for the entire view.
    

remove_item(_item_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.remove_item "Permalink to this definition")

Removes an item from the action row.

This function returns the class instance to allow for fluent-style chaining.

Parameters

**item** ([`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")) – The item to remove from the action row.

find_item(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.find_item "Permalink to this definition")

Gets an item with [`Item.id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item.id "discord.ui.Item.id") set as `id`, or `None` if not found.

Warning

This is **not the same** as `custom_id`.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the component.

Returns

The item found, or `None`.

Return type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

clear_items()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.clear_items "Permalink to this definition")

Removes all items from the action row.

This function returns the class instance to allow for fluent-style chaining.

button(_*_, _label=None_, _custom_id=None_, _disabled=False_, _style=<ButtonStyle.secondary: 2>_, _emoji=None_, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.button "Permalink to this definition")

A decorator that attaches a button to the action row.

The function being decorated should have three parameters, `self` representing the [`discord.ui.ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "discord.ui.ActionRow"), the [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") you receive and the [`discord.ui.Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button") being pressed.

Note

Buttons with a URL or a SKU cannot be created with this function. Consider creating a [`Button`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Button "discord.ui.Button") manually and adding it via [`ActionRow.add_item()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.add_item "discord.ui.ActionRow.add_item") instead. This is beacuse these buttons cannot have a callback associated with them since Discord does not do any processing with them.

Parameters

*   **label** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The label of the button, if any. Can only be up to 80 characters.
    
*   **custom_id** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The ID of the button that gets received during an interaction. It is recommended to not set this parameters to prevent conflicts. Can only be up to 100 characters.
    
*   **style** ([`ButtonStyle`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle "discord.ButtonStyle")) – The style of the button. Defaults to [`ButtonStyle.grey`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ButtonStyle.grey "discord.ButtonStyle.grey").
    
*   **disabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the button is disabled or not. Defaults to `False`.
    
*   **emoji** (Optional[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji"), [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji")]]) – The emoji of the button. This can be in string form or a [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji") or a full [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji").
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The ID of the component. This must be unique across the view.
    
    New in version 2.6.
    

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within this item that checks whether the callback should be processed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

New in version 2.4.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the callback should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.parent "Permalink to this definition")

This item’s parent, if applicable. Only available on items with children.

New in version 2.6.

Type

Optional[[`Item`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Item "discord.ui.Item")]

_property_ view[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.view "Permalink to this definition")

The underlying view for this item.

Type

Optional[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

select(_*_, _cls=discord.ui.select.Select[typing.Any]_, _options=..._, _channel_types=..._, _placeholder=None_, _custom_id=..._, _min_values=1_, _max_values=1_, _disabled=False_, _default_values=..._, _id=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow.select "Permalink to this definition")

A decorator that attaches a select menu to the action row.

The function being decorated should have three parameters, `self` representing the [`discord.ui.ActionRow`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ActionRow "discord.ui.ActionRow"), the [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") you receive and the chosen select class.

To obtain the selected values inside the callback, you can use the `values` attribute of the chosen class in the callback. The list of values will depend on the type of select menu used. View the table below for more information.

Example

content_copy

```
class MyView(discord.ui.LayoutView):
    action_row = discord.ui.ActionRow()

 @action_row.select(cls=ChannelSelect, channel_types=[discord.ChannelType.text])
    async def select_channels(self, interaction: discord.Interaction, select: ChannelSelect):
        return await interaction.response.send_message(f'You selected {select.values[0].mention}')
```

Parameters

*   **cls** (Union[Type[[`discord.ui.Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select")], Type[[`discord.ui.UserSelect`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.UserSelect "discord.ui.UserSelect")], Type[[`discord.ui.RoleSelect`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.RoleSelect "discord.ui.RoleSelect")], Type[[`discord.ui.MentionableSelect`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MentionableSelect "discord.ui.MentionableSelect")], Type[[`discord.ui.ChannelSelect`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ChannelSelect "discord.ui.ChannelSelect")]]) – The class to use for the select menu. Defaults to [`discord.ui.Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select"). You can use other select types to display different select menus to the user. See the table above for the different values you can get from each select type. Subclasses work as well, however the callback in the subclass will get overridden.
    
*   **placeholder** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The placeholder text that is shown if nothing is selected, if any. Can only be up to 150 characters.
    
*   **custom_id** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The ID of the select menu that gets received during an interaction. It is recommended not to set this parameter to prevent conflicts. Can only be up to 100 characters.
    
*   **min_values** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The minimum number of items that must be chosen for this select menu. Defaults to 1 and must be between 0 and 25.
    
*   **max_values** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The maximum number of items that must be chosen for this select menu. Defaults to 1 and must be between 1 and 25.
    
*   **options** (List[[`discord.SelectOption`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.SelectOption "discord.SelectOption")]) – A list of options that can be selected in this menu. This can only be used with [`Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select") instances. Can only contain up to 25 items.
    
*   **channel_types** (List[[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")]) – The types of channels to show in the select menu. Defaults to all channels. This can only be used with [`ChannelSelect`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.ChannelSelect "discord.ui.ChannelSelect") instances.
    
*   **disabled** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the select is disabled or not. Defaults to `False`.
    
*   **default_values** (Sequence[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – A list of objects representing the default values for the select menu. This cannot be used with regular [`Select`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.Select "discord.ui.Select") instances. If `cls` is [`MentionableSelect`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.MentionableSelect "discord.ui.MentionableSelect") and [`Object`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Object "discord.Object") is passed, then the type must be specified in the constructor. Number of items must be in range of `min_values` and `max_values`.
    
*   **id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The ID of the component. This must be unique across the view.
    
    New in version 2.6.
    

## Application Commands[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#application-commands "Permalink to this headline")

The library has helpers to aid in creation of application commands. These are all in the `discord.app_commands` package.

### CommandTree[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#commandtree "Permalink to this headline")

_class_ discord.app_commands.CommandTree(_client_, _*_, _fallback_to_global=True_, _allowed_contexts=..._, _allowed_installs=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "Permalink to this definition")

Represents a container that holds application command information.

Parameters

*   **client** ([`Client`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client "discord.Client")) – The client instance to get application command information from.
    
*   **fallback_to_global** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If a guild-specific command is not found when invoked, then try falling back into a global command in the tree. For example, if the tree locally has a `/ping` command under the global namespace but the guild has a guild-specific `/ping`, instead of failing to find the guild-specific `/ping` command it will fall back to the global `/ping` command. This has the potential to raise more [`CommandSignatureMismatch`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandSignatureMismatch "discord.app_commands.CommandSignatureMismatch") errors than usual. Defaults to `True`.
    
*   **allowed_contexts** ([`AppCommandContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "discord.app_commands.AppCommandContext")) –
    
    The default allowed contexts that applies to all commands in this tree. Note that you can override this on a per command basis.
    
    New in version 2.4.
    
*   **allowed_installs** ([`AppInstallationType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType "discord.app_commands.AppInstallationType")) –
    
    The default allowed install locations that apply to all commands in this tree. Note that you can override this on a per command basis.
    
    New in version 2.4.
    

@command(_*_, _name=..._, _description=..._, _nsfw=False_, _guild=..._, _guilds=..._, _auto_locale_strings=True_, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.command "Permalink to this definition")

A decorator that creates an application command from a regular function directly under this tree.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the application command. If not given, it defaults to a lower-case version of the callback name.
    
*   **description** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The description of the application command. This shows up in the UI to describe the application command. If not given, it defaults to the first line of the docstring of the callback shortened to 100 characters.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    The guild to add the command to. If not given or `None` then it becomes a global command instead.
    
*   **guilds** (List[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    The list of guilds to add the command to. This cannot be mixed with the `guild` parameter. If no guilds are given at all then it becomes a global command instead.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

@context_menu(_*_, _name=..._, _nsfw=False_, _guild=..._, _guilds=..._, _auto_locale_strings=True_, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.context_menu "Permalink to this definition")

A decorator that creates an application command context menu from a regular function directly under this tree.

This function must have a signature of [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") as its first parameter and taking either a [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member"), [`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User"), or [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message"), or a [`typing.Union`](https://docs.python.org/3/library/typing.html#typing.Union "(in Python v3.13)") of `Member` and `User` as its second parameter.

Examples

content_copy

```
@app_commands.context_menu()
async def react(interaction: discord.Interaction, message: discord.Message):
    await interaction.response.send_message('Very cool message!', ephemeral=True)

@app_commands.context_menu()
async def ban(interaction: discord.Interaction, user: discord.Member):
    await interaction.response.send_message(f'Should I actually ban {user}...', ephemeral=True)
```

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the context menu command. If not given, it defaults to a title-case version of the callback name. Note that unlike regular slash commands this can have spaces and upper case characters in the name.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    The guild to add the command to. If not given or `None` then it becomes a global command instead.
    
*   **guilds** (List[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    The list of guilds to add the command to. This cannot be mixed with the `guild` parameter. If no guilds are given at all then it becomes a global command instead.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

@error(_coro_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

This must match the signature of the [`on_error()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.on_error "discord.app_commands.CommandTree.on_error") callback.

The error passed will be derived from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine or does not match the signature.

_await_ fetch_command(_command_id_, _/_, _*_, _guild=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.fetch_command "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Fetches an application command from the application.

Parameters

*   **command_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the command to fetch.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to fetch the command from. If not passed then the global command is fetched instead.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the command failed.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The application command was not found. This could also be because the command is a guild command and the guild was not specified and vice versa.
    

Returns

The application command.

Return type

[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand")

_await_ fetch_commands(_*_, _guild=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.fetch_commands "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Fetches the application’s current commands.

If no guild is passed then global commands are fetched, otherwise the guild’s commands are fetched instead.

Note

This includes context menu commands.

Parameters

**guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to fetch the commands from. If not passed then global commands are fetched instead.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the commands failed.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    

Returns

The application’s commands.

Return type

List[[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand")]

copy_global_to(_*_, _guild_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.copy_global_to "Permalink to this definition")

Copies all global commands to the specified guild.

This method is mainly available for development purposes, as it allows you to copy your global commands over to a testing guild easily.

Note that this method will _override_ pre-existing guild commands that would conflict.

Parameters

**guild** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The guild to copy the commands to.

Raises

[**CommandLimitReached**](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandLimitReached "discord.app_commands.CommandLimitReached") – The maximum number of commands was reached for that guild. This is currently 100 for slash commands and 5 for context menu commands.

add_command(_command_, _/_, _*_, _guild=..._, _guilds=..._, _override=False_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.add_command "Permalink to this definition")

Adds an application command to the tree.

This only adds the command locally – in order to sync the commands and enable them in the client, [`sync()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "discord.app_commands.CommandTree.sync") must be called.

The root parent of the command is added regardless of the type passed.

Parameters

*   **command** (Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]) – The application command or group to add.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    The guild to add the command to. If not given or `None` then it becomes a global command instead.
    
*   **guilds** (List[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    The list of guilds to add the command to. This cannot be mixed with the `guild` parameter. If no guilds are given at all then it becomes a global command instead.
    
*   **override** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to override a command with the same name. If `False` an exception is raised. Default is `False`.
    

Raises

*   [**CommandAlreadyRegistered**](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandAlreadyRegistered "discord.app_commands.CommandAlreadyRegistered") – The command was already registered and no override was specified.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The application command passed is not a valid application command. Or, `guild` and `guilds` were both given.
    
*   [**CommandLimitReached**](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandLimitReached "discord.app_commands.CommandLimitReached") – The maximum number of commands was reached globally or for that guild. This is currently 100 for slash commands and 5 for context menu commands.
    

remove_command(_command_, _/_, _*_, _guild=None_, _type=<AppCommandType.chat_input: 1>_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.remove_command "Permalink to this definition")

Removes an application command from the tree.

This only removes the command locally – in order to sync the commands and remove them in the client, [`sync()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "discord.app_commands.CommandTree.sync") must be called.

Parameters

*   **command** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the root command to remove.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to remove the command from. If not given or `None` then it removes a global command instead.
    
*   **type** ([`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")) – The type of command to remove. Defaults to [`chat_input`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType.chat_input "discord.AppCommandType.chat_input"), i.e. slash commands.
    

Returns

The application command that got removed. If nothing was removed then `None` is returned instead.

Return type

Optional[Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

clear_commands(_*_, _guild_, _type=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.clear_commands "Permalink to this definition")

Clears all application commands from the tree.

This only removes the commands locally – in order to sync the commands and remove them in the client, [`sync()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "discord.app_commands.CommandTree.sync") must be called.

Parameters

*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to remove the commands from. If `None` then it removes all global commands instead.
    
*   **type** ([`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")) – The type of command to clear. If not given or `None` then it removes all commands regardless of the type.
    

get_command(_command_, _/_, _*_, _guild=None_, _type=<AppCommandType.chat_input: 1>_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.get_command "Permalink to this definition")

Gets an application command from the tree.

Parameters

*   **command** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the root command to get.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to get the command from. If not given or `None` then it gets a global command instead.
    
*   **type** ([`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")) – The type of command to get. Defaults to [`chat_input`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType.chat_input "discord.AppCommandType.chat_input"), i.e. slash commands.
    

Returns

The application command that was found. If nothing was found then `None` is returned instead.

Return type

Optional[Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

get_commands(_*_, _guild=None_, _type=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.get_commands "Permalink to this definition")

Gets all application commands from the tree.

Parameters

*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to get the commands from, not including global commands. If not given or `None` then only global commands are returned.
    
*   **type** (Optional[[`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")]) – The type of commands to get. When not given or `None`, then all command types are returned.
    

Returns

The application commands from the tree.

Return type

List[Union[[`ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu"), [`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

_for ... in_ walk_commands(_*_, _guild=None_, _type=<AppCommandType.chat_input: 1>_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.walk_commands "Permalink to this definition")

An iterator that recursively walks through all application commands and child commands from the tree.

Parameters

*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to iterate the commands from, not including global commands. If not given or `None` then only global commands are iterated.
    
*   **type** ([`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")) – The type of commands to iterate over. Defaults to [`chat_input`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType.chat_input "discord.AppCommandType.chat_input"), i.e. slash commands.
    

Yields

Union[[`ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu"), [`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")] – The application commands from the tree.

_await_ on_error(_interaction_, _error_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.on_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when any command raises an [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

The default implementation logs the exception using the library logger if the command does not have any error handlers attached to it.

To get the command that failed, [`discord.Interaction.command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.command "discord.Interaction.command") should be used.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that is being handled.
    
*   **error** ([`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError")) – The exception that was raised.
    

_property_ translator[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.translator "Permalink to this definition")

The translator, if any, responsible for handling translation of commands.

To change the translator, use [`set_translator()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.set_translator "discord.app_commands.CommandTree.set_translator").

Type

Optional[[`Translator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "discord.app_commands.Translator")]

_await_ set_translator(_translator_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.set_translator "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Sets the translator to use for translating commands.

If a translator was previously set, it will be unloaded using its [`Translator.unload()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.unload "discord.app_commands.Translator.unload") method.

When a translator is set, it will be loaded using its [`Translator.load()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.load "discord.app_commands.Translator.load") method.

Parameters

**translator** (Optional[[`Translator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "discord.app_commands.Translator")]) – The translator to use. If `None` then the translator is just removed and unloaded.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The translator was not `None` or a [`Translator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "discord.app_commands.Translator") instance.

_await_ sync(_*_, _guild=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Syncs the application commands to Discord.

This also runs the translator to get the translated strings necessary for feeding back into Discord.

This must be called for the application commands to show up.

Parameters

**guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to sync the commands to. If `None` then it syncs all global commands instead.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Syncing the commands failed.
    
*   [**CommandSyncFailure**](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandSyncFailure "discord.app_commands.CommandSyncFailure") – Syncing the commands failed due to a user related error, typically because the command has invalid data. This is equivalent to an HTTP status code of 400.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – The client does not have the `applications.commands` scope in the guild.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The client does not have an application ID.
    
*   [**TranslationError**](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationError "discord.app_commands.TranslationError") – An error occurred while translating the commands.
    

Returns

The application’s commands that got synced.

Return type

List[[`AppCommand`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommand "discord.app_commands.AppCommand")]

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A global check to determine if an [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") should be processed by the tree.

The default implementation returns True (all interactions are processed), but can be overridden if custom behaviour is desired.

### Commands[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#commands "Permalink to this headline")

#### Command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#command "Permalink to this headline")

_class_ discord.app_commands.Command(_*_, _name_, _description_, _callback_, _nsfw=False_, _parent=None_, _guild_ids=None_, _allowed_contexts=None_, _allowed_installs=None_, _auto_locale_strings=True_, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "Permalink to this definition")

A class that implements an application command.

These are usually not created manually, instead they are created using one of the following decorators:

*   [`command()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.command "discord.app_commands.command")
    
*   [`Group.command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.command "discord.app_commands.Group.command")
    
*   [`CommandTree.command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.command "discord.app_commands.CommandTree.command")
    

New in version 2.0.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the application command.
    
*   **description** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The description of the application command. This shows up in the UI to describe the application command.
    
*   **callback** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine that is executed when the command is called.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **parent** (Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]) – The parent application command. `None` if there isn’t one.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.name "Permalink to this definition")

The name of the application command.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.description "Permalink to this definition")

The description of the application command. This shows up in the UI to describe the application command.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

checks[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.checks "Permalink to this definition")

A list of predicates that take a [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") parameter to indicate whether the command callback should be executed. If an exception is necessary to be thrown to signal failure, then one inherited from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError") should be used. If all the checks fail without propagating an exception, [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure") is raised.

default_permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.default_permissions "Permalink to this definition")

The default permissions that can execute this command on Discord. Note that server administrators can override this value in the client. Setting an empty permissions field will disallow anyone except server administrators from using the command in a guild.

Due to a Discord limitation, this does not work on subcommands.

Type

Optional[[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")]

guild_only[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.guild_only "Permalink to this definition")

Whether the command should only be usable in guild contexts.

Due to a Discord limitation, this does not work on subcommands.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

allowed_contexts[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.allowed_contexts "Permalink to this definition")

The contexts that the command is allowed to be used in. Overrides `guild_only` if this is set.

New in version 2.4.

Type

Optional[[`AppCommandContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "discord.app_commands.AppCommandContext")]

allowed_installs[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.allowed_installs "Permalink to this definition")

The installation contexts that the command is allowed to be installed on.

New in version 2.4.

Type

Optional[[`AppInstallationType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType "discord.app_commands.AppInstallationType")]

nsfw[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.nsfw "Permalink to this definition")

Whether the command is NSFW and should only work in NSFW channels.

Due to a Discord limitation, this does not work on subcommands.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.parent "Permalink to this definition")

The parent application command. `None` if there isn’t one.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]

extras[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.extras "Permalink to this definition")

A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

@autocomplete(_name_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.autocomplete "Permalink to this definition")

A decorator that registers a coroutine as an autocomplete prompt for a parameter.

The coroutine callback must have 2 parameters, the [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction"), and the current value by the user (the string currently being typed by the user).

To get the values from other parameters that may be filled in, accessing [`Interaction.namespace`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.namespace "discord.Interaction.namespace") will give a [`Namespace`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Namespace "discord.app_commands.Namespace") object with those values.

Parent [`checks`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") are ignored within an autocomplete. However, checks can be added to the autocomplete callback and the ones added will be called. If the checks fail for any reason then an empty list is sent as the interaction response.

The coroutine decorator **must** return a list of [`Choice`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "discord.app_commands.Choice") objects. Only up to 25 objects are supported.

Warning

The choices returned from this coroutine are suggestions. The user may ignore them and input their own value.

Example:

content_copy

```
@app_commands.command()
async def fruits(interaction: discord.Interaction, fruit: str):
    await interaction.response.send_message(f'Your favourite fruit seems to be {fruit}')

@fruits.autocomplete('fruit')
async def fruits_autocomplete( interaction: discord.Interaction, current: str, ) -> List[app_commands.Choice[str]]:
    fruits = ['Banana', 'Pineapple', 'Apple', 'Watermelon', 'Melon', 'Cherry']
    return [
        app_commands.Choice(name=fruit, value=fruit)
        for fruit in fruits if current.lower() in fruit.lower()
    ]
```

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The parameter name to register as autocomplete.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine or the parameter is not found or of an invalid type.

@error(_coro_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

The local error handler is called whenever an exception is raised in the body of the command or during handling of the command. The error handler must take 2 parameters, the interaction and the error.

The error passed will be derived from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

_property_ callback[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.callback "Permalink to this definition")

The coroutine that is executed when the command is called.

Type

[coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")

_property_ parameters[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.parameters "Permalink to this definition")

Returns a list of parameters for this command.

This does not include the `self` or `interaction` parameters.

Returns

The parameters of this command.

Return type

List[[`Parameter`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter "discord.app_commands.Parameter")]

get_parameter(_name_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.get_parameter "Permalink to this definition")

Retrieves a parameter by its name.

The name must be the Python identifier rather than the renamed one for display on Discord.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The parameter name in the callback function.

Returns

The parameter or `None` if not found.

Return type

Optional[[`Parameter`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter "discord.app_commands.Parameter")]

_property_ root_parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.root_parent "Permalink to this definition")

The root parent of this command.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.qualified_name "Permalink to this definition")

Returns the fully qualified command name.

The qualified name includes the parent name as well. For example, in a command like `/foo bar` the qualified name is `foo bar`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

add_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.add_check "Permalink to this definition")

Adds a check to the command.

This is the non-decorator interface to [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check").

Parameters

**func** – The function that will be used as a check.

remove_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.remove_check "Permalink to this definition")

Removes a check from the command.

This function is idempotent and will not raise an exception if the function is not in the command’s checks.

Parameters

**func** – The function to remove from the checks.

#### Parameter[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#parameter "Permalink to this headline")

_class_ discord.app_commands.Parameter[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter "Permalink to this definition")

A class that contains the parameter information of a [`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command") callback.

New in version 2.0.

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.name "Permalink to this definition")

The name of the parameter. This is the Python identifier for the parameter.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

display_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.display_name "Permalink to this definition")

The displayed name of the parameter on Discord.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.description "Permalink to this definition")

The description of the parameter.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

autocomplete[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.autocomplete "Permalink to this definition")

Whether the parameter has an autocomplete handler.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

locale_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.locale_name "Permalink to this definition")

The display name’s locale string, if available.

Type

Optional[[`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]

locale_description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.locale_description "Permalink to this definition")

The description’s locale string, if available.

Type

Optional[[`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]

required[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.required "Permalink to this definition")

Whether the parameter is required

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

choices[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.choices "Permalink to this definition")

A list of choices this parameter takes, if any.

Type

List[[`Choice`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "discord.app_commands.Choice")]

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.type "Permalink to this definition")

The underlying type of this parameter.

Type

[`AppCommandOptionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "discord.AppCommandOptionType")

channel_types[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.channel_types "Permalink to this definition")

The channel types that are allowed for this parameter.

Type

List[[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")]

min_value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.min_value "Permalink to this definition")

The minimum supported value for this parameter.

Type

Optional[Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]]

max_value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.max_value "Permalink to this definition")

The maximum supported value for this parameter.

Type

Optional[Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]]

default[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.default "Permalink to this definition")

The default value of the parameter, if given. If not given then this is [`MISSING`](https://discordpy.readthedocs.io/en/stable/api.html#discord.utils.MISSING "discord.utils.MISSING").

Type

Any

command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Parameter.command "Permalink to this definition")

The command this parameter is attached to.

Type

[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command")

#### Group[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#group "Permalink to this headline")

_class_ discord.app_commands.Group(_*_, _name=..._, _description=..._, _parent=None_, _guild_ids=None_, _guild_only=..._, _allowed_contexts=..._, _allowed_installs=..._, _nsfw=..._, _auto_locale_strings=True_, _default_permissions=..._, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "Permalink to this definition")

A class that implements an application command group.

These are usually inherited rather than created manually.

Decorators such as [`guild_only()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guild_only "discord.app_commands.guild_only"), [`guilds()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guilds "discord.app_commands.guilds"), and [`default_permissions()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.default_permissions "discord.app_commands.default_permissions") will apply to the group if used on top of a subclass. For example:

content_copy

```
from discord import app_commands

@app_commands.guild_only()
class MyGroup(app_commands.Group):
    pass
```

New in version 2.0.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the group. If not given, it defaults to a lower-case kebab-case version of the class name.
    
*   **description** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The description of the group. This shows up in the UI to describe the group. If not given, it defaults to the docstring of the class shortened to 100 characters.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **default_permissions** (Optional[[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")]) –
    
    The default permissions that can execute this group on Discord. Note that server administrators can override this value in the client. Setting an empty permissions field will disallow anyone except server administrators from using the command in a guild.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **guild_only** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the group should only be usable in guild contexts. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **parent** (Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]) – The parent application command. `None` if there isn’t one.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.name "Permalink to this definition")

The name of the group.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.description "Permalink to this definition")

The description of the group. This shows up in the UI to describe the group.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

default_permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.default_permissions "Permalink to this definition")

The default permissions that can execute this group on Discord. Note that server administrators can override this value in the client. Setting an empty permissions field will disallow anyone except server administrators from using the command in a guild.

Due to a Discord limitation, this does not work on subcommands.

Type

Optional[[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")]

guild_only[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.guild_only "Permalink to this definition")

Whether the group should only be usable in guild contexts.

Due to a Discord limitation, this does not work on subcommands.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

allowed_contexts[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.allowed_contexts "Permalink to this definition")

The contexts that this group is allowed to be used in. Overrides guild_only if set.

New in version 2.4.

Type

Optional[[`AppCommandContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "discord.app_commands.AppCommandContext")]

allowed_installs[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.allowed_installs "Permalink to this definition")

The installation contexts that the command is allowed to be installed on.

New in version 2.4.

Type

Optional[[`AppInstallationType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType "discord.app_commands.AppInstallationType")]

nsfw[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.nsfw "Permalink to this definition")

Whether the command is NSFW and should only work in NSFW channels.

Due to a Discord limitation, this does not work on subcommands.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.parent "Permalink to this definition")

The parent group. `None` if there isn’t one.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]

extras[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.extras "Permalink to this definition")

A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

@command(_*_, _name=..._, _description=..._, _nsfw=False_, _auto_locale_strings=True_, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.command "Permalink to this definition")

A decorator that creates an application command from a regular function under this group.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the application command. If not given, it defaults to a lower-case version of the callback name.
    
*   **description** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The description of the application command. This shows up in the UI to describe the application command. If not given, it defaults to the first line of the docstring of the callback shortened to 100 characters.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

@error(_coro_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

The local error handler is called whenever an exception is raised in a child command. The error handler must take 2 parameters, the interaction and the error.

The error passed will be derived from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine, or is an invalid coroutine.

_property_ root_parent[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.root_parent "Permalink to this definition")

The parent of this group.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.qualified_name "Permalink to this definition")

Returns the fully qualified group name.

The qualified name includes the parent name as well. For example, in a group like `/foo bar` the qualified name is `foo bar`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ commands[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.commands "Permalink to this definition")

The commands that this group contains.

Type

List[Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

_for ... in_ walk_commands()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.walk_commands "Permalink to this definition")

An iterator that recursively walks through all commands that this group contains.

Yields

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")] – The commands in this group.

_await_ on_error(_interaction_, _error_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.on_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when a child’s command raises an [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

To get the command that failed, [`discord.Interaction.command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.command "discord.Interaction.command") should be used.

The default implementation does nothing.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that is being handled.
    
*   **error** ([`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError")) – The exception that was raised.
    

_await_ interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.interaction_check "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A callback that is called when an interaction happens within the group that checks whether a command inside the group should be executed.

This is useful to override if, for example, you want to ensure that the interaction author is a given user.

The default implementation of this returns `True`.

Note

If an exception occurs within the body then the check is considered a failure and error handlers such as [`on_error()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.on_error "discord.app_commands.Group.on_error") is called. See [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError") for more information.

Parameters

**interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that occurred.

Returns

Whether the view children’s callbacks should be called.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

add_command(_command_, _/_, _*_, _override=False_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.add_command "Permalink to this definition")

Adds a command or group to this group’s internal list of commands.

Parameters

*   **command** (Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]) – The command or group to add.
    
*   **override** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to override a pre-existing command or group with the same name. If `False` then an exception is raised.
    

Raises

*   [**CommandAlreadyRegistered**](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandAlreadyRegistered "discord.app_commands.CommandAlreadyRegistered") – The command or group is already registered. Note that the [`CommandAlreadyRegistered.guild_id`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandAlreadyRegistered.guild_id "discord.app_commands.CommandAlreadyRegistered.guild_id") attribute will always be `None` in this case.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – There are too many commands already registered or the group is too deeply nested.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The wrong command type was passed.
    

remove_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.remove_command "Permalink to this definition")

Removes a command or group from the internal list of commands.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command or group to remove.

Returns

The command that was removed. If nothing was removed then `None` is returned instead.

Return type

Optional[Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

get_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.get_command "Permalink to this definition")

Retrieves a command or group from its name.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command or group to retrieve.

Returns

The command or group that was retrieved. If nothing was found then `None` is returned instead.

Return type

Optional[Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

### Decorators[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#decorators "Permalink to this headline")

@discord.app_commands.command(_*_, _name=..._, _description=..._, _nsfw=False_, _auto_locale_strings=True_, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.command "Permalink to this definition")

Creates an application command from a regular function.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the application command. If not given, it defaults to a lower-case version of the callback name.
    
*   **description** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The description of the application command. This shows up in the UI to describe the application command. If not given, it defaults to the first line of the docstring of the callback shortened to 100 characters.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

@discord.app_commands.context_menu(_*_, _name=..._, _nsfw=False_, _auto_locale_strings=True_, _extras=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.context_menu "Permalink to this definition")

Creates an application command context menu from a regular function.

This function must have a signature of [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") as its first parameter and taking either a [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member"), [`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User"), or [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message"), or a [`typing.Union`](https://docs.python.org/3/library/typing.html#typing.Union "(in Python v3.13)") of `Member` and `User` as its second parameter.

Examples

content_copy

```
@app_commands.context_menu()
async def react(interaction: discord.Interaction, message: discord.Message):
    await interaction.response.send_message('Very cool message!', ephemeral=True)

@app_commands.context_menu()
async def ban(interaction: discord.Interaction, user: discord.Member):
    await interaction.response.send_message(f'Should I actually ban {user}...', ephemeral=True)
```

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the context menu command. If not given, it defaults to a title-case version of the callback name. Note that unlike regular slash commands this can have spaces and upper case characters in the name.
    
*   **nsfw** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the command is NSFW and should only work in NSFW channels. Defaults to `False`.
    
    Due to a Discord limitation, this does not work on subcommands.
    
*   **auto_locale_strings** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). This could avoid some repetition and be more ergonomic for certain defaults such as default command names, command descriptions, and parameter names. Defaults to `True`.
    
*   **extras** ([`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")) – A dictionary that can be used to store extraneous data. The library will not touch any values or keys within this dictionary.
    

@discord.app_commands.describe(_**parameters_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.describe "Permalink to this definition")

Describes the given parameters by their name using the key of the keyword argument as the name.

Example:

content_copy

```
@app_commands.command(description='Bans a member')
@app_commands.describe(member='the member to ban')
async def ban(interaction: discord.Interaction, member: discord.Member):
    await interaction.response.send_message(f'Banned {member}')
```

Alternatively, you can describe parameters using Google, Sphinx, or Numpy style docstrings.

Example:

content_copy

```
@app_commands.command()
async def ban(interaction: discord.Interaction, member: discord.Member):
 """Bans a member  Parameters  -----------  member: discord.Member  the member to ban  """
    await interaction.response.send_message(f'Banned {member}')
```

Parameters

****parameters** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The description of the parameters.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The parameter name is not found.

@discord.app_commands.rename(_**parameters_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.rename "Permalink to this definition")

Renames the given parameters by their name using the key of the keyword argument as the name.

This renames the parameter within the Discord UI. When referring to the parameter in other decorators, the parameter name used in the function is used instead of the renamed one.

Example:

content_copy

```
@app_commands.command()
@app_commands.rename(the_member_to_ban='member')
async def ban(interaction: discord.Interaction, the_member_to_ban: discord.Member):
    await interaction.response.send_message(f'Banned {the_member_to_ban}')
```

Parameters

****parameters** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name of the parameters.

Raises

*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The parameter name is already used by another parameter.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The parameter name is not found.
    

@discord.app_commands.choices(_**parameters_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.choices "Permalink to this definition")

Instructs the given parameters by their name to use the given choices for their choices.

Example:

content_copy

```
@app_commands.command()
@app_commands.describe(fruits='fruits to choose from')
@app_commands.choices(fruits=[
    Choice(name='apple', value=1),
    Choice(name='banana', value=2),
    Choice(name='cherry', value=3),
])
async def fruit(interaction: discord.Interaction, fruits: Choice[int]):
    await interaction.response.send_message(f'Your favourite fruit is {fruits.name}.')
```

Note

This is not the only way to provide choices to a command. There are two more ergonomic ways of doing this. The first one is to use a [`typing.Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.13)") annotation:

content_copy

```
@app_commands.command()
@app_commands.describe(fruits='fruits to choose from')
async def fruit(interaction: discord.Interaction, fruits: Literal['apple', 'banana', 'cherry']):
    await interaction.response.send_message(f'Your favourite fruit is {fruits}.')
```

The second way is to use an [`enum.Enum`](https://docs.python.org/3/library/enum.html#enum.Enum "(in Python v3.13)"):

content_copy

```
class Fruits(enum.Enum):
    apple = 1
    banana = 2
    cherry = 3

@app_commands.command()
@app_commands.describe(fruits='fruits to choose from')
async def fruit(interaction: discord.Interaction, fruits: Fruits):
    await interaction.response.send_message(f'Your favourite fruit is {fruits}.')
```

Parameters

****parameters** – The choices of the parameters.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The parameter name is not found or the parameter type was incorrect.

@discord.app_commands.autocomplete(_**parameters_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.autocomplete "Permalink to this definition")

Associates the given parameters with the given autocomplete callback.

Autocomplete is only supported on types that have [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), or [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)") values.

[`Checks`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") are supported, however they must be attached to the autocomplete callback in order to work. Checks attached to the command are ignored when invoking the autocomplete callback.

For more information, see the [`Command.autocomplete()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.autocomplete "discord.app_commands.Command.autocomplete") documentation.

Warning

The choices returned from this coroutine are suggestions. The user may ignore them and input their own value.

Example:

content_copy

```
async def fruit_autocomplete( interaction: discord.Interaction, current: str, ) -> List[app_commands.Choice[str]]:
    fruits = ['Banana', 'Pineapple', 'Apple', 'Watermelon', 'Melon', 'Cherry']
    return [
        app_commands.Choice(name=fruit, value=fruit)
        for fruit in fruits if current.lower() in fruit.lower()
    ]

@app_commands.command()
@app_commands.autocomplete(fruit=fruit_autocomplete)
async def fruits(interaction: discord.Interaction, fruit: str):
    await interaction.response.send_message(f'Your favourite fruit seems to be {fruit}')
```

Parameters

****parameters** – The parameters to mark as autocomplete.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The parameter name is not found or the parameter type was incorrect.

@discord.app_commands.guilds(_*guild_ids_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guilds "Permalink to this definition")

Associates the given guilds with the command.

When the command instance is added to a [`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree"), the guilds that are specified by this decorator become the default guilds that it’s added to rather than being a global command.

If no arguments are given, then the command will not be synced anywhere. This may be modified later using the [`CommandTree.add_command()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.add_command "discord.app_commands.CommandTree.add_command") method.

Example:

content_copy

```
MY_GUILD_ID = discord.Object(...)  # Guild ID here

@app_commands.command()
@app_commands.guilds(MY_GUILD_ID)
async def bonk(interaction: discord.Interaction):
    await interaction.response.send_message('Bonk', ephemeral=True)
```

Parameters

***guild_ids** (Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guilds to associate this command with. The command tree will use this as the default when added rather than adding it as a global command.

@discord.app_commands.guild_only(_func=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guild_only "Permalink to this definition")

A decorator that indicates this command can only be used in a guild context.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side. Therefore, there is no error handler called when a command is used within a private message.

This decorator can be called with or without parentheses.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

Examples

content_copy

```
@app_commands.command()
@app_commands.guild_only()
async def my_guild_only_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am only available in guilds!')
```

@discord.app_commands.dm_only(_func=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.dm_only "Permalink to this definition")

A decorator that indicates this command can only be used in the context of bot DMs.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side. Therefore, there is no error handler called when a command is used within a guild or group DM.

This decorator can be called with or without parentheses.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

Examples

content_copy

```
@app_commands.command()
@app_commands.dm_only()
async def my_dm_only_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am only available in DMs!')
```

@discord.app_commands.private_channel_only(_func=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.private_channel_only "Permalink to this definition")

A decorator that indicates this command can only be used in the context of DMs and group DMs.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side. Therefore, there is no error handler called when a command is used within a guild.

This decorator can be called with or without parentheses.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

New in version 2.4.

Examples

content_copy

```
@app_commands.command()
@app_commands.private_channel_only()
async def my_private_channel_only_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am only available in DMs and GDMs!')
```

@discord.app_commands.allowed_contexts(_guilds=..._, _dms=..._, _private_channels=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.allowed_contexts "Permalink to this definition")

A decorator that indicates this command can only be used in certain contexts. Valid contexts are guilds, DMs and private channels.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

New in version 2.4.

Examples

content_copy

```
@app_commands.command()
@app_commands.allowed_contexts(guilds=True, dms=False, private_channels=True)
async def my_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am only available in guilds and private channels!')
```

@discord.app_commands.user_install(_func=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.user_install "Permalink to this definition")

A decorator that indicates this command should be installed for users.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

New in version 2.4.

Examples

content_copy

```
@app_commands.command()
@app_commands.user_install()
async def my_user_install_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am installed in users by default!')
```

@discord.app_commands.guild_install(_func=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guild_install "Permalink to this definition")

A decorator that indicates this command should be installed in guilds.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

New in version 2.4.

Examples

content_copy

```
@app_commands.command()
@app_commands.guild_install()
async def my_guild_install_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am installed in guilds by default!')
```

@discord.app_commands.allowed_installs(_guilds=..._, _users=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.allowed_installs "Permalink to this definition")

A decorator that indicates this command should be installed in certain contexts. Valid contexts are guilds and users.

This is **not** implemented as a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"), and is instead verified by Discord server side.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

New in version 2.4.

Examples

content_copy

```
@app_commands.command()
@app_commands.allowed_installs(guilds=False, users=True)
async def my_command(interaction: discord.Interaction) -> None:
    await interaction.response.send_message('I am installed in users by default!')
```

@discord.app_commands.default_permissions(_perms_obj=None_, _/_, _**perms_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.default_permissions "Permalink to this definition")

A decorator that sets the default permissions needed to execute this command.

When this decorator is used, by default users must have these permissions to execute the command. However, an administrator can change the permissions needed to execute this command using the official client. Therefore, this only serves as a hint.

Setting an empty permissions field, including via calling this with no arguments, will disallow anyone except server administrators from using the command in a guild.

This is sent to Discord server side, and is not a [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check"). Therefore, error handlers are not called.

Due to a Discord limitation, this decorator does nothing in subcommands and is ignored.

Warning

This serves as a _hint_ and members are _not_ required to have the permissions given to actually execute this command. If you want to ensure that members have the permissions needed, consider using [`has_permissions()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_permissions "discord.app_commands.checks.has_permissions") instead.

Parameters

*   ****perms** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Keyword arguments denoting the permissions to set as the default.
    
*   **perms_obj** ([`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")) –
    
    A permissions object as positional argument. This can be used in combination with `**perms`.
    
    New in version 2.5.
    

Examples

content_copy

```
@app_commands.command()
@app_commands.default_permissions(manage_messages=True)
async def test(interaction: discord.Interaction):
    await interaction.response.send_message('You may or may not have manage messages.')
```

content_copy

```
ADMIN_PERMS = discord.Permissions(administrator=True)

@app_commands.command()
@app_commands.default_permissions(ADMIN_PERMS, manage_messages=True)
async def test(interaction: discord.Interaction):
    await interaction.response.send_message('You may or may not have manage messages.')
```

### Checks[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#checks "Permalink to this headline")

@discord.app_commands.check(_predicate_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "Permalink to this definition")

A decorator that adds a check to an application command.

These checks should be predicates that take in a single parameter taking a [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction"). If the check returns a `False`-like value then during invocation a [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure") exception is raised and sent to the appropriate error handlers.

These checks can be either a coroutine or not.

Examples

Creating a basic check to see if the command invoker is you.

content_copy

```
def check_if_it_is_me(interaction: discord.Interaction) -> bool:
    return interaction.user.id == 85309593344815104

@tree.command()
@app_commands.check(check_if_it_is_me)
async def only_for_me(interaction: discord.Interaction):
    await interaction.response.send_message('I know you!', ephemeral=True)
```

Transforming common checks into its own decorator:

content_copy

```
def is_me():
    def predicate(interaction: discord.Interaction) -> bool:
        return interaction.user.id == 85309593344815104
    return app_commands.check(predicate)

@tree.command()
@is_me()
async def only_me(interaction: discord.Interaction):
    await interaction.response.send_message('Only you!')
```

Parameters

**predicate** (Callable[[[`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")], [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – The predicate to check if the command should be invoked.

@discord.app_commands.checks.has_role(_item_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_role "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") that is added that checks if the member invoking the command has the role specified via the name or ID specified.

If a string is specified, you must give the exact name of the role, including caps and spelling.

If an integer is specified, you must give the exact snowflake ID of the role.

This check raises one of two special exceptions, [`MissingRole`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingRole "discord.app_commands.MissingRole") if the user is missing a role, or [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.NoPrivateMessage "discord.app_commands.NoPrivateMessage") if it is used in a private message. Both inherit from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

Note

This is different from the permission system that Discord provides for application commands. This is done entirely locally in the program rather than being handled by Discord.

Parameters

**item** (Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The name or ID of the role to check.

@discord.app_commands.checks.has_any_role(_*items_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_any_role "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") that is added that checks if the member invoking the command has **any** of the roles specified. This means that if they have one out of the three roles specified, then this check will return `True`.

Similar to [`has_role()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_role "discord.app_commands.checks.has_role"), the names or IDs passed in must be exact.

This check raises one of two special exceptions, [`MissingAnyRole`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingAnyRole "discord.app_commands.MissingAnyRole") if the user is missing all roles, or [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.NoPrivateMessage "discord.app_commands.NoPrivateMessage") if it is used in a private message. Both inherit from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

Note

This is different from the permission system that Discord provides for application commands. This is done entirely locally in the program rather than being handled by Discord.

Parameters

**items** (List[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]) – An argument list of names or IDs to check that the member has roles wise.

Example

content_copy

```
@tree.command()
@app_commands.checks.has_any_role('Library Devs', 'Moderators', 492212595072434186)
async def cool(interaction: discord.Interaction):
    await interaction.response.send_message('You are cool indeed')
```

@discord.app_commands.checks.has_permissions(_**perms_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_permissions "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") that is added that checks if the member has all of the permissions necessary.

Note that this check operates on the permissions given by [`discord.Interaction.permissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.permissions "discord.Interaction.permissions").

The permissions passed in must be exactly like the properties shown under [`discord.Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions").

This check raises a special exception, [`MissingPermissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingPermissions "discord.app_commands.MissingPermissions") that is inherited from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

Note

This is different from the permission system that Discord provides for application commands. This is done entirely locally in the program rather than being handled by Discord.

Parameters

****perms** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Keyword arguments denoting the permissions to check for.

Example

content_copy

```
@tree.command()
@app_commands.checks.has_permissions(manage_messages=True)
async def test(interaction: discord.Interaction):
    await interaction.response.send_message('You can manage messages.')
```

@discord.app_commands.checks.bot_has_permissions(_**perms_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.bot_has_permissions "Permalink to this definition")

Similar to [`has_permissions()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_permissions "discord.app_commands.checks.has_permissions") except checks if the bot itself has the permissions listed. This relies on [`discord.Interaction.app_permissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.app_permissions "discord.Interaction.app_permissions").

This check raises a special exception, [`BotMissingPermissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.BotMissingPermissions "discord.app_commands.BotMissingPermissions") that is inherited from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

@discord.app_commands.checks.cooldown(_rate_, _per_, _*_, _key=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.cooldown "Permalink to this definition")

A decorator that adds a cooldown to a command.

A cooldown allows a command to only be used a specific amount of times in a specific time frame. These cooldowns are based off of the `key` function provided. If a `key` is not provided then it defaults to a user-level cooldown. The `key` function must take a single parameter, the [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") and return a value that is used as a key to the internal cooldown mapping.

The `key` function can optionally be a coroutine.

If a cooldown is triggered, then [`CommandOnCooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandOnCooldown "discord.app_commands.CommandOnCooldown") is raised to the error handlers.

Examples

Setting a one per 5 seconds per member cooldown on a command:

content_copy

```
@tree.command()
@app_commands.checks.cooldown(1, 5.0, key=lambda i: (i.guild_id, i.user.id))
async def test(interaction: discord.Interaction):
    await interaction.response.send_message('Hello')

@test.error
async def on_test_error(interaction: discord.Interaction, error: app_commands.AppCommandError):
    if isinstance(error, app_commands.CommandOnCooldown):
        await interaction.response.send_message(str(error), ephemeral=True)
```

Parameters

*   **rate** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The number of times a command can be used before triggering a cooldown.
    
*   **per** ([`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")) – The amount of seconds to wait for a cooldown when it’s been triggered.
    
*   **key** (Optional[Callable[[[`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")], [`collections.abc.Hashable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Hashable "(in Python v3.13)")]]) – A function that returns a key to the mapping denoting the type of cooldown. Can optionally be a coroutine. If not given then defaults to a user-level cooldown. If `None` is passed then it is interpreted as a “global” cooldown.
    

@discord.app_commands.checks.dynamic_cooldown(_factory_, _*_, _key=..._)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.dynamic_cooldown "Permalink to this definition")

A decorator that adds a dynamic cooldown to a command.

A cooldown allows a command to only be used a specific amount of times in a specific time frame. These cooldowns are based off of the `key` function provided. If a `key` is not provided then it defaults to a user-level cooldown. The `key` function must take a single parameter, the [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") and return a value that is used as a key to the internal cooldown mapping.

If a `factory` function is given, it must be a function that accepts a single parameter of type [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction") and must return a [`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown") or `None`. If `None` is returned then that cooldown is effectively bypassed.

Both `key` and `factory` can optionally be coroutines.

If a cooldown is triggered, then [`CommandOnCooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandOnCooldown "discord.app_commands.CommandOnCooldown") is raised to the error handlers.

Examples

Setting a cooldown for everyone but the owner.

content_copy

```
def cooldown_for_everyone_but_me(interaction: discord.Interaction) -> Optional[app_commands.Cooldown]:
    if interaction.user.id == 80088516616269824:
        return None
    return app_commands.Cooldown(1, 10.0)

@tree.command()
@app_commands.checks.dynamic_cooldown(cooldown_for_everyone_but_me)
async def test(interaction: discord.Interaction):
    await interaction.response.send_message('Hello')

@test.error
async def on_test_error(interaction: discord.Interaction, error: app_commands.AppCommandError):
    if isinstance(error, app_commands.CommandOnCooldown):
        await interaction.response.send_message(str(error), ephemeral=True)
```

Parameters

*   **factory** (Optional[Callable[[[`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")], Optional[[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")]]]) – A function that takes an interaction and returns a cooldown that will apply to that interaction or `None` if the interaction should not have a cooldown.
    
*   **key** (Optional[Callable[[[`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")], [`collections.abc.Hashable`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Hashable "(in Python v3.13)")]]) – A function that returns a key to the mapping denoting the type of cooldown. Can optionally be a coroutine. If not given then defaults to a user-level cooldown. If `None` is passed then it is interpreted as a “global” cooldown.
    

### Cooldown[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#cooldown "Permalink to this headline")

_class_ discord.app_commands.Cooldown(_rate_, _per_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "Permalink to this definition")

Represents a cooldown for a command.

New in version 2.0.

rate[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.rate "Permalink to this definition")

The total number of tokens available per [`per`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.per "discord.app_commands.Cooldown.per") seconds.

Type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

per[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.per "Permalink to this definition")

The length of the cooldown period in seconds.

Type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

get_tokens(_current=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.get_tokens "Permalink to this definition")

Returns the number of available tokens before rate limiting is applied.

Parameters

**current** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The time in seconds since Unix epoch to calculate tokens at. If not supplied then [`time.time()`](https://docs.python.org/3/library/time.html#time.time "(in Python v3.13)") is used.

Returns

The number of tokens available before the cooldown is to be applied.

Return type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

get_retry_after(_current=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.get_retry_after "Permalink to this definition")

Returns the time in seconds until the cooldown will be reset.

Parameters

**current** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The current time in seconds since Unix epoch. If not supplied, then [`time.time()`](https://docs.python.org/3/library/time.html#time.time "(in Python v3.13)") is used.

Returns

The number of seconds to wait before this cooldown will be reset.

Return type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

update_rate_limit(_current=None_, _*_, _tokens=1_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.update_rate_limit "Permalink to this definition")

Updates the cooldown rate limit.

Parameters

*   **current** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The time in seconds since Unix epoch to update the rate limit at. If not supplied, then [`time.time()`](https://docs.python.org/3/library/time.html#time.time "(in Python v3.13)") is used.
    
*   **tokens** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The amount of tokens to deduct from the rate limit.
    

Returns

The retry-after time in seconds if rate limited.

Return type

Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]

reset()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.reset "Permalink to this definition")

Reset the cooldown to its initial state.

copy()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown.copy "Permalink to this definition")

Creates a copy of this cooldown.

Returns

A new instance of this cooldown.

Return type

[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")

### Namespace[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#namespace "Permalink to this headline")

_class_ discord.app_commands.Namespace[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Namespace "Permalink to this definition")

An object that holds the parameters being passed to a command in a mostly raw state.

This class is deliberately simple and just holds the option name and resolved value as a simple key-pair mapping. These attributes can be accessed using dot notation. For example, an option with the name of `example` can be accessed using `ns.example`. If an attribute is not found, then `None` is returned rather than an attribute error.

Warning

The key names come from the raw Discord data, which means that if a parameter was renamed then the renamed key is used instead of the function parameter name.

New in version 2.0.

x == y

Checks if two namespaces are equal by checking if all attributes are equal.

x != y

Checks if two namespaces are not equal.

x[key]

Returns an attribute if it is found, otherwise raises a [`KeyError`](https://docs.python.org/3/library/exceptions.html#KeyError "(in Python v3.13)").

key in x

Checks if the attribute is in the namespace.

iter(x)

Returns an iterator of `(name, value)` pairs. This allows it to be, for example, constructed as a dict or a list of pairs.

This namespace object converts resolved objects into their appropriate form depending on their type. Consult the table below for conversion information.

Note

In autocomplete interactions, the namespace might not be validated or filled in. Discord does not send the resolved data as well, so this means that certain fields end up just as IDs rather than the resolved data. In these cases, a [`discord.Object`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Object "discord.Object") is returned instead.

This is a Discord limitation.

### Transformers[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#transformers "Permalink to this headline")

#### Transformer[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#transformer "Permalink to this headline")

_class_ discord.app_commands.Transformer(_*args_, _**kwds_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "Permalink to this definition")

The base class that allows a type annotation in an application command parameter to map into a [`AppCommandOptionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "discord.AppCommandOptionType") and transform the raw value into one from this type.

This class is customisable through the overriding of methods and properties in the class and by using it as the second type parameter of the [`Transform`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transform "discord.app_commands.Transform") class. For example, to convert a string into a custom pair type:

content_copy

```
class Point(typing.NamedTuple):
    x: int
    y: int

class PointTransformer(app_commands.Transformer):
    async def transform(self, interaction: discord.Interaction, value: str) -> Point:
        (x, _, y) = value.partition(',')
        return Point(x=int(x.strip()), y=int(y.strip()))

@app_commands.command()
async def graph( interaction: discord.Interaction, point: app_commands.Transform[Point, PointTransformer], ):
    await interaction.response.send_message(str(point))
```

If a class is passed instead of an instance to the second type parameter, then it is constructed with no arguments passed to the `__init__` method.

New in version 2.0.

_property_ type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.type "Permalink to this definition")

The option type associated with this transformer.

This must be a [`property`](https://docs.python.org/3/library/functions.html#property "(in Python v3.13)").

Defaults to [`string`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.string "discord.AppCommandOptionType.string").

Type

[`AppCommandOptionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "discord.AppCommandOptionType")

_property_ channel_types[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.channel_types "Permalink to this definition")

A list of channel types that are allowed to this parameter.

Only valid if the [`type()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.type "discord.app_commands.Transformer.type") returns [`channel`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.channel "discord.AppCommandOptionType.channel").

This must be a [`property`](https://docs.python.org/3/library/functions.html#property "(in Python v3.13)").

Defaults to an empty list.

Type

List[[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")]

_property_ min_value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.min_value "Permalink to this definition")

The minimum supported value for this parameter.

Only valid if the [`type()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.type "discord.app_commands.Transformer.type") returns [`number`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.number "discord.AppCommandOptionType.number") [`integer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.integer "discord.AppCommandOptionType.integer"), or [`string`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.string "discord.AppCommandOptionType.string").

This must be a [`property`](https://docs.python.org/3/library/functions.html#property "(in Python v3.13)").

Defaults to `None`.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ max_value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.max_value "Permalink to this definition")

The maximum supported value for this parameter.

Only valid if the [`type()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.type "discord.app_commands.Transformer.type") returns [`number`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.number "discord.AppCommandOptionType.number") [`integer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.integer "discord.AppCommandOptionType.integer"), or [`string`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.string "discord.AppCommandOptionType.string").

This must be a [`property`](https://docs.python.org/3/library/functions.html#property "(in Python v3.13)").

Defaults to `None`.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_property_ choices[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.choices "Permalink to this definition")

A list of up to 25 choices that are allowed to this parameter.

Only valid if the [`type()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.type "discord.app_commands.Transformer.type") returns [`number`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.number "discord.AppCommandOptionType.number") [`integer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.integer "discord.AppCommandOptionType.integer"), or [`string`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.string "discord.AppCommandOptionType.string").

This must be a [`property`](https://docs.python.org/3/library/functions.html#property "(in Python v3.13)").

Defaults to `None`.

Type

Optional[List[[`Choice`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "discord.app_commands.Choice")]]

_await_ transform(_interaction_, _value_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.transform "Permalink to this definition")

This function _could be a_ [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Transforms the converted option value into another value.

The value passed into this transform function is the same as the one in the [`conversion table`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Namespace "discord.app_commands.Namespace").

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction being handled.
    
*   **value** (_Any_) – The value of the given argument after being resolved. See the [`conversion table`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Namespace "discord.app_commands.Namespace") for how certain option types correspond to certain values.
    

_await_ autocomplete(_interaction_, _value_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer.autocomplete "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

An autocomplete prompt handler to be automatically used by options using this transformer.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The autocomplete interaction being handled.
    
*   **value** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The current value entered by the user.
    

Returns

A list of choices to be displayed to the user, a maximum of 25.

Return type

List[[`Choice`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Choice "discord.app_commands.Choice")]

#### Transform[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#transform "Permalink to this headline")

_class_ discord.app_commands.Transform[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transform "Permalink to this definition")

A type annotation that can be applied to a parameter to customise the behaviour of an option type by transforming with the given [`Transformer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "discord.app_commands.Transformer"). This requires the usage of two generic parameters, the first one is the type you’re converting to and the second one is the type of the [`Transformer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "discord.app_commands.Transformer") actually doing the transformation.

During type checking time this is equivalent to [`typing.Annotated`](https://docs.python.org/3/library/typing.html#typing.Annotated "(in Python v3.13)") so type checkers understand the intent of the code.

For example usage, check [`Transformer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "discord.app_commands.Transformer").

New in version 2.0.

#### Range[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#range "Permalink to this headline")

_class_ discord.app_commands.Range[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Range "Permalink to this definition")

A type annotation that can be applied to a parameter to require a numeric or string type to fit within the range provided.

During type checking time this is equivalent to [`typing.Annotated`](https://docs.python.org/3/library/typing.html#typing.Annotated "(in Python v3.13)") so type checkers understand the intent of the code.

Some example ranges:

*   `Range[int, 10]` means the minimum is 10 with no maximum.
    
*   `Range[int, None, 10]` means the maximum is 10 with no minimum.
    
*   `Range[int, 1, 10]` means the minimum is 1 and the maximum is 10.
    
*   `Range[float, 1.0, 5.0]` means the minimum is 1.0 and the maximum is 5.0.
    
*   `Range[str, 1, 10]` means the minimum length is 1 and the maximum length is 10.
    

New in version 2.0.

Examples

content_copy

```
@app_commands.command()
async def range(interaction: discord.Interaction, value: app_commands.Range[int, 10, 12]):
    await interaction.response.send_message(f'Your value is {value}', ephemeral=True)
```

### Translations[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#translations "Permalink to this headline")

#### Translator[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#translator "Permalink to this headline")

_class_ discord.app_commands.Translator[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "Permalink to this definition")

A class that handles translations for commands, parameters, and choices.

Translations are done lazily in order to allow for async enabled translations as well as supporting a wide array of translation systems such as [`gettext`](https://docs.python.org/3/library/gettext.html#module-gettext "(in Python v3.13)") and [Project Fluent](https://projectfluent.org/).

In order for a translator to be used, it must be set using the [`CommandTree.set_translator()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.set_translator "discord.app_commands.CommandTree.set_translator") method. The translation flow for a string is as follows:

1.  Use [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") instead of [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)") in areas of a command you want to be translated.
    
    *   Currently, these are command names, command descriptions, parameter names, parameter descriptions, and choice names.
        
    *   This can also be used inside the [`describe()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.describe "discord.app_commands.describe") decorator.
        
    
2.  Call [`CommandTree.set_translator()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.set_translator "discord.app_commands.CommandTree.set_translator") to the translator instance that will handle the translations.
    
3.  Call [`CommandTree.sync()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "discord.app_commands.CommandTree.sync")
    
4.  The library will call [`Translator.translate()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.translate "discord.app_commands.Translator.translate") on all the relevant strings being translated.
    

New in version 2.0.

_await_ load()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.load "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

An asynchronous setup function for loading the translation system.

The default implementation does nothing.

This is invoked when [`CommandTree.set_translator()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.set_translator "discord.app_commands.CommandTree.set_translator") is called.

_await_ unload()[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.unload "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

An asynchronous teardown function for unloading the translation system.

The default implementation does nothing.

This is invoked when [`CommandTree.set_translator()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.set_translator "discord.app_commands.CommandTree.set_translator") is called if a tree already has a translator or when [`discord.Client.close()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.close "discord.Client.close") is called.

_await_ translate(_string_, _locale_, _context_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.translate "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Translates the given string to the specified locale.

If the string cannot be translated, `None` should be returned.

The default implementation returns `None`.

If an exception is raised in this method, it should inherit from [`TranslationError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationError "discord.app_commands.TranslationError"). If it doesn’t, then when this is called the exception will be chained with it instead.

Parameters

*   **string** ([`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")) – The string being translated.
    
*   **locale** ([`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale")) – The locale being requested for translation.
    
*   **context** ([`TranslationContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContext "discord.app_commands.TranslationContext")) – The translation context where the string originated from. For better type checking ergonomics, the `TranslationContextTypes` type can be used instead to aid with type narrowing. It is functionally equivalent to [`TranslationContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContext "discord.app_commands.TranslationContext").
    

#### locale_str[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#locale-str "Permalink to this headline")

_class_ discord.app_commands.locale_str(_message_, _/_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "Permalink to this definition")

Marks a string as ready for translation.

This is done lazily and is not actually translated until [`CommandTree.sync()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "discord.app_commands.CommandTree.sync") is called.

The sync method then ultimately defers the responsibility of translating to the [`Translator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "discord.app_commands.Translator") instance used by the [`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree"). For more information on the translation flow, see the [`Translator`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator "discord.app_commands.Translator") documentation.

str(x)

Returns the message passed to the string.

x == y

Checks if the string is equal to another string.

x != y

Checks if the string is not equal to another string.

hash(x)

Returns the hash of the string.

New in version 2.0.

message[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str.message "Permalink to this definition")

The message being translated. Once set, this cannot be changed.

Warning

This must be the default “message” that you send to Discord. Discord sends this message back to the library and the library uses it to access the data in order to dispatch commands.

For example, in a command name context, if the command name is `foo` then the message _must_ also be `foo`. For other translation systems that require a message ID such as Fluent, consider using a keyword argument to pass it in.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

extras[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str.extras "Permalink to this definition")

A dict of user provided extras to attach to the translated string. This can be used to add more context, information, or any metadata necessary to aid in actually translating the string.

Since these are passed via keyword arguments, the keys are strings.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

#### TranslationContext[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#translationcontext "Permalink to this headline")

_class_ discord.app_commands.TranslationContext(_location_, _data_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContext "Permalink to this definition")

A class that provides context for the [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") being translated.

This is useful to determine where exactly the string is located and aid in looking up the actual translation.

location[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContext.location "Permalink to this definition")

The location where this string is located.

Type

[`TranslationContextLocation`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation "discord.app_commands.TranslationContextLocation")

data[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContext.data "Permalink to this definition")

The extraneous data that is being translated.

Type

Any

#### TranslationContextLocation[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#translationcontextlocation "Permalink to this headline")

_class_ discord.app_commands.TranslationContextLocation[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation "Permalink to this definition")

An enum representing the location context that the translation occurs in when requested for translation.

New in version 2.0.

command_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.command_name "Permalink to this definition")

The translation involved a command name.

command_description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.command_description "Permalink to this definition")

The translation involved a command description.

group_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.group_name "Permalink to this definition")

The translation involved a group name.

group_description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.group_description "Permalink to this definition")

The translation involved a group description.

parameter_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.parameter_name "Permalink to this definition")

The translation involved a parameter name.

parameter_description[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.parameter_description "Permalink to this definition")

The translation involved a parameter description.

choice_name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.choice_name "Permalink to this definition")

The translation involved a choice name.

other[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContextLocation.other "Permalink to this definition")

The translation involved something else entirely. This is useful for running [`Translator.translate()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.translate "discord.app_commands.Translator.translate") for custom usage.

### Exceptions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#exceptions "Permalink to this headline")

_exception_ discord.app_commands.AppCommandError[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "Permalink to this definition")

The base exception type for all application command related errors.

This inherits from [`discord.DiscordException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.DiscordException "discord.DiscordException").

This exception and exceptions inherited from it are handled in a special way as they are caught and passed into various error handlers in this order:

*   [`Command.error`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.error "discord.app_commands.Command.error")
    
*   [`Group.on_error`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group.on_error "discord.app_commands.Group.on_error")
    
*   [`CommandTree.on_error`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.on_error "discord.app_commands.CommandTree.on_error")
    

New in version 2.0.

_exception_ discord.app_commands.CommandInvokeError(_command_, _e_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandInvokeError "Permalink to this definition")

An exception raised when the command being invoked raised an exception.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

New in version 2.0.

original[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandInvokeError.original "Permalink to this definition")

The original exception that was raised. You can also get this via the `__cause__` attribute.

Type

[`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")

command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandInvokeError.command "Permalink to this definition")

The command that failed.

Type

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu")]

_exception_ discord.app_commands.TransformerError(_value_, _opt_type_, _transformer_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TransformerError "Permalink to this definition")

An exception raised when a [`Transformer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "discord.app_commands.Transformer") or type annotation fails to convert to its target type.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

If an exception occurs while converting that does not subclass [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError") then the exception is wrapped into this exception. The original exception can be retrieved using the `__cause__` attribute. Otherwise if the exception derives from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError") then it will be propagated as-is.

New in version 2.0.

value[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TransformerError.value "Permalink to this definition")

The value that failed to convert.

Type

Any

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TransformerError.type "Permalink to this definition")

The type of argument that failed to convert.

Type

[`AppCommandOptionType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType "discord.AppCommandOptionType")

transformer[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TransformerError.transformer "Permalink to this definition")

The transformer that failed the conversion.

Type

[`Transformer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "discord.app_commands.Transformer")

_exception_ discord.app_commands.TranslationError(_*msg_, _string=None_, _locale=None_, _context_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationError "Permalink to this definition")

An exception raised when the library fails to translate a string.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

If an exception occurs while calling [`Translator.translate()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Translator.translate "discord.app_commands.Translator.translate") that does not subclass this then the exception is wrapped into this exception. The original exception can be retrieved using the `__cause__` attribute. Otherwise it will be propagated as-is.

New in version 2.0.

string[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationError.string "Permalink to this definition")

The string that caused the error, if any.

Type

Optional[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]]

locale[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationError.locale "Permalink to this definition")

The locale that caused the error, if any.

Type

Optional[[`Locale`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Locale "discord.Locale")]

context[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationError.context "Permalink to this definition")

The context of the translation that triggered the error.

Type

[`TranslationContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.TranslationContext "discord.app_commands.TranslationContext")

_exception_ discord.app_commands.CheckFailure[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "Permalink to this definition")

An exception raised when check predicates in a command have failed.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

New in version 2.0.

_exception_ discord.app_commands.NoPrivateMessage(_message=None_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.NoPrivateMessage "Permalink to this definition")

An exception raised when a command does not work in a direct message.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

_exception_ discord.app_commands.MissingRole(_missing_role_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingRole "Permalink to this definition")

An exception raised when the command invoker lacks a role to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

missing_role[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingRole.missing_role "Permalink to this definition")

The required role that is missing. This is the parameter passed to [`has_role()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_role "discord.app_commands.checks.has_role").

Type

Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_exception_ discord.app_commands.MissingAnyRole(_missing_roles_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingAnyRole "Permalink to this definition")

An exception raised when the command invoker lacks any of the roles specified to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

missing_roles[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingAnyRole.missing_roles "Permalink to this definition")

The roles that the invoker is missing. These are the parameters passed to [`has_any_role()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.checks.has_any_role "discord.app_commands.checks.has_any_role").

Type

List[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]

_exception_ discord.app_commands.MissingPermissions(_missing_permissions_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingPermissions "Permalink to this definition")

An exception raised when the command invoker lacks permissions to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

missing_permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.MissingPermissions.missing_permissions "Permalink to this definition")

The required permissions that are missing.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.app_commands.BotMissingPermissions(_missing_permissions_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.BotMissingPermissions "Permalink to this definition")

An exception raised when the bot’s member lacks permissions to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

missing_permissions[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.BotMissingPermissions.missing_permissions "Permalink to this definition")

The required permissions that are missing.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.app_commands.CommandOnCooldown(_cooldown_, _retry_after_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandOnCooldown "Permalink to this definition")

An exception raised when the command being invoked is on cooldown.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CheckFailure "discord.app_commands.CheckFailure").

New in version 2.0.

cooldown[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandOnCooldown.cooldown "Permalink to this definition")

The cooldown that was triggered.

Type

[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")

retry_after[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandOnCooldown.retry_after "Permalink to this definition")

The amount of seconds to wait before you can retry again.

Type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

_exception_ discord.app_commands.CommandLimitReached(_guild_id_, _limit_, _type=<AppCommandType.chat_input: 1>_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandLimitReached "Permalink to this definition")

An exception raised when the maximum number of application commands was reached either globally or in a guild.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

New in version 2.0.

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandLimitReached.type "Permalink to this definition")

The type of command that reached the limit.

Type

[`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandLimitReached.guild_id "Permalink to this definition")

The guild ID that reached the limit or `None` if it was global.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

limit[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandLimitReached.limit "Permalink to this definition")

The limit that was hit.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

_exception_ discord.app_commands.CommandAlreadyRegistered(_name_, _guild_id_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandAlreadyRegistered "Permalink to this definition")

An exception raised when a command is already registered.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

New in version 2.0.

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandAlreadyRegistered.name "Permalink to this definition")

The name of the command already registered.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

guild_id[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandAlreadyRegistered.guild_id "Permalink to this definition")

The guild ID this command was already registered at. If `None` then it was a global command.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_exception_ discord.app_commands.CommandSignatureMismatch(_command_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandSignatureMismatch "Permalink to this definition")

An exception raised when an application command from Discord has a different signature from the one provided in the code. This happens because your command definition differs from the command definition you provided Discord. Either your code is out of date or the data from Discord is out of sync.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

New in version 2.0.

command[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandSignatureMismatch.command "Permalink to this definition")

The command that had the signature mismatch.

Type

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`ContextMenu`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.ContextMenu "discord.app_commands.ContextMenu"), [`Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]

_exception_ discord.app_commands.CommandNotFound(_name_, _parents_, _type=<AppCommandType.chat_input: 1>_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandNotFound "Permalink to this definition")

An exception raised when an application command could not be found.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError").

New in version 2.0.

name[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandNotFound.name "Permalink to this definition")

The name of the application command not found.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

parents[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandNotFound.parents "Permalink to this definition")

A list of parent command names that were previously found prior to the application command not being found.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

type[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandNotFound.type "Permalink to this definition")

The type of command that was not found.

Type

[`AppCommandType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandType "discord.AppCommandType")

_exception_ discord.app_commands.CommandSyncFailure(_child_, _commands_)[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandSyncFailure "Permalink to this definition")

An exception raised when [`CommandTree.sync()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.sync "discord.app_commands.CommandTree.sync") failed.

This provides syncing failures in a slightly more readable format.

This inherits from [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError") and [`HTTPException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException").

New in version 2.0.

#### Exception Hierarchy[¶](https://discordpy.readthedocs.io/en/stable/interactions/api.html#exception-hierarchy "Permalink to this headline")