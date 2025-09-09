---
url: https://discordpy.readthedocs.io/en/stable/ext/commands/api.html
time: 2025-09-21P23:36:11
tags: 
---
The following section outlines the API of discord.py’s command extension module.

## Bots[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#bots "Permalink to this headline")

### Bot[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#bot "Permalink to this headline")

_class_ discord.ext.commands.Bot(_command_prefix_, _*_, _help_command=<default-help-command>_, _tree_cls=<class 'discord.app_commands.tree.CommandTree'>_, _description=None_, _allowed_contexts=..._, _allowed_installs=..._, _intents_, _**options_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot "Permalink to this definition")

Represents a Discord bot.

This class is a subclass of [`discord.Client`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client "discord.Client") and as a result anything that you can do with a [`discord.Client`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client "discord.Client") you can do with this bot.

This class also subclasses [`GroupMixin`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin "discord.ext.commands.GroupMixin") to provide the functionality to manage commands.

Unlike [`discord.Client`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client "discord.Client"), this class does not require manually setting a [`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree") and is automatically set upon instantiating the class.

async with x

Asynchronously initialises the bot and automatically cleans up.

New in version 2.0.

command_prefix[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.command_prefix "Permalink to this definition")

The command prefix is what the message content must contain initially to have a command invoked. This prefix could either be a string to indicate what the prefix should be, or a callable that takes in the bot as its first parameter and [`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") as its second parameter and returns the prefix. This is to facilitate “dynamic” command prefixes. This callable can be either a regular function or a coroutine.

An empty string as the prefix always matches, enabling prefix-less command invocation. While this may be useful in DMs it should be avoided in servers, as it’s likely to cause performance issues and unintended command invocations.

The command prefix could also be an iterable of strings indicating that multiple checks for the prefix should be used and the first one to match will be the invocation prefix. You can get this prefix via [`Context.prefix`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.prefix "discord.ext.commands.Context.prefix").

Note

When passing multiple prefixes be careful to not pass a prefix that matches a longer prefix occurring later in the sequence. For example, if the command prefix is `('!', '!?')` the `'!?'` prefix will never be matched to any message as the previous one matches messages starting with `!?`. This is especially important when passing an empty string, it should always be last as no prefix after it will be matched.

case_insensitive[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.case_insensitive "Permalink to this definition")

Whether the commands should be case insensitive. Defaults to `False`. This attribute does not carry over to groups. You must set it to every group if you require group commands to be case insensitive as well.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.description "Permalink to this definition")

The content prefixed into the default help message.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

help_command[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.help_command "Permalink to this definition")

The help command implementation to use. This can be dynamically set at runtime. To remove the help command pass `None`. For more information on implementing a help command, see [Help Commands](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#ext-commands-help-command).

Type

Optional[[`HelpCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand "discord.ext.commands.HelpCommand")]

owner_id[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.owner_id "Permalink to this definition")

The user ID that owns the bot. If this is not set and is then queried via [`is_owner()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_owner "discord.ext.commands.Bot.is_owner") then it is fetched automatically using [`application_info()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application_info "discord.ext.commands.Bot.application_info").

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

owner_ids[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.owner_ids "Permalink to this definition")

The user IDs that owns the bot. This is similar to [`owner_id`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.owner_id "discord.ext.commands.Bot.owner_id"). If this is not set and the application is team based, then it is fetched automatically using [`application_info()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application_info "discord.ext.commands.Bot.application_info"). For performance reasons it is recommended to use a [`set`](https://docs.python.org/3/library/stdtypes.html#set "(in Python v3.13)") for the collection. You cannot set both `owner_id` and `owner_ids`.

New in version 1.3.

Type

Optional[Collection[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]

strip_after_prefix[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.strip_after_prefix "Permalink to this definition")

Whether to strip whitespace characters after encountering the command prefix. This allows for `!   hello` and `!hello` to both work if the `command_prefix` is set to `!`. Defaults to `False`.

New in version 1.7.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

tree_cls[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.tree_cls "Permalink to this definition")

The type of application command tree to use. Defaults to [`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree").

New in version 2.0.

Type

Type[[`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree")]

allowed_contexts[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.allowed_contexts "Permalink to this definition")

The default allowed contexts that applies to all application commands in the application command tree.

Note that you can override this on a per command basis.

New in version 2.4.

Type

[`AppCommandContext`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandContext "discord.app_commands.AppCommandContext")

allowed_installs[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.allowed_installs "Permalink to this definition")

The default allowed install locations that apply to all application commands in the application command tree.

Note that you can override this on a per command basis.

New in version 2.4.

Type

[`AppInstallationType`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppInstallationType "discord.app_commands.AppInstallationType")

@after_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.after_invoke "Permalink to this definition")

A decorator that registers a coroutine as a post-invoke hook.

A post-invoke hook is called directly after the command is called. This makes it a useful function to clean-up database connections or any type of clean up required.

This post-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

Note

Similar to [`before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "discord.ext.commands.Bot.before_invoke"), this is not called unless checks and argument parsing procedures succeed. This hook is, however, **always** called regardless of the internal command callback raising an error (i.e. [`CommandInvokeError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandInvokeError "discord.ext.commands.CommandInvokeError")). This makes it ideal for clean-up scenarios.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the post-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@before_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "Permalink to this definition")

A decorator that registers a coroutine as a pre-invoke hook.

A pre-invoke hook is called directly before the command is called. This makes it a useful function to set up database connections or any type of set up required.

This pre-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

Note

The [`before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "discord.ext.commands.Bot.before_invoke") and [`after_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.after_invoke "discord.ext.commands.Bot.after_invoke") hooks are only called if all checks and argument parsing procedures pass without error. If any check or argument parsing procedures fail then the hooks are not called.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the pre-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@check[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check "Permalink to this definition")

A decorator that adds a global check to the bot.

A global check is similar to a [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that is applied on a per command basis except it is run before any command checks have been verified and applies to every command the bot has.

Note

This function can either be a regular function or a coroutine.

Similar to a command [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check"), this takes a single parameter of type [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") and can only raise exceptions inherited from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Example

content_copy

```
@bot.check
def check_commands(ctx):
    return ctx.command.qualified_name in allowed_commands
```

Changed in version 2.0: `func` parameter is now positional-only.

@check_once[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check_once "Permalink to this definition")

A decorator that adds a “call once” global check to the bot.

Unlike regular global checks, this one is called only once per [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "discord.ext.commands.Bot.invoke") call.

Regular global checks are called whenever a command is called or [`Command.can_run()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.can_run "discord.ext.commands.Command.can_run") is called. This type of check bypasses that and ensures that it’s called only once, even inside the default help command.

Note

When using this function the [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") sent to a group subcommand may only parse the parent command and not the subcommands due to it being invoked once per [`Bot.invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "discord.ext.commands.Bot.invoke") call.

Note

This function can either be a regular function or a coroutine.

Similar to a command [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check"), this takes a single parameter of type [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") and can only raise exceptions inherited from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Example

content_copy

```
@bot.check_once
def whitelist(ctx):
    return ctx.message.author.id in my_whitelist
```

Changed in version 2.0: `func` parameter is now positional-only.

@command(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.command "Permalink to this definition")

A shortcut decorator that invokes [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Command, adds it to the bot, then returns it.

Return type

Callable[…, [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

@event[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.event "Permalink to this definition")

A decorator that registers an event to listen to.

You can find more info about the events on the [documentation below](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-events).

The events must be a [coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)"), if not, [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") is raised.

Example

content_copy

```
@client.event
async def on_ready():
    print('Ready!')
```

Changed in version 2.0: `coro` parameter is now positional-only.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@group(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.group "Permalink to this definition")

A shortcut decorator that invokes [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.group "discord.ext.commands.group") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Group, adds it to the bot, then returns it.

Return type

Callable[…, [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

@hybrid_command(_name=..._, _with_app_command=True_, _*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.hybrid_command "Permalink to this definition")

A shortcut decorator that invokes [`hybrid_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.hybrid_command "discord.ext.commands.hybrid_command") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_command "discord.ext.commands.Bot.add_command").

Returns

A decorator that converts the provided method into a Command, adds it to the bot, then returns it.

Return type

Callable[…, [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand")]

@hybrid_group(_name=..._, _with_app_command=True_, _*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.hybrid_group "Permalink to this definition")

A shortcut decorator that invokes [`hybrid_group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.hybrid_group "discord.ext.commands.hybrid_group") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_command "discord.ext.commands.Bot.add_command").

Returns

A decorator that converts the provided method into a Group, adds it to the bot, then returns it.

Return type

Callable[…, [`HybridGroup`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup "discord.ext.commands.HybridGroup")]

@listen(_name=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.listen "Permalink to this definition")

A decorator that registers another function as an external event listener. Basically this allows you to listen to multiple events from different places e.g. such as [`on_ready()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.on_ready "discord.on_ready")

The functions being listened to must be a [coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)").

Example

content_copy

```
@bot.listen()
async def on_message(message):
    print('one')

# in some other file...

@bot.listen('on_message')
async def my_message(message):
    print('two')
```

Would print one and two in an unspecified order.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The function being listened to is not a coroutine.

_property_ activity[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.activity "Permalink to this definition")

The activity being used upon logging in.

Type

Optional[[`BaseActivity`](https://discordpy.readthedocs.io/en/stable/api.html#discord.BaseActivity "discord.BaseActivity")]

add_check(_func_, _/_, _*_, _call_once=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_check "Permalink to this definition")

Adds a global check to the bot.

This is the non-decorator interface to [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check "discord.ext.commands.Bot.check") and [`check_once()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check_once "discord.ext.commands.Bot.check_once").

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

*   **func** – The function that was used as a global check.
    
*   **call_once** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If the function should only be called once per [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "discord.ext.commands.Bot.invoke") call.
    

_await_ add_cog(_cog_, _/_, _*_, _override=False_, _guild=..._, _guilds=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_cog "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Adds a “cog” to the bot.

A cog is a class that has its own event listeners and commands.

If the cog is a [`app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group") then it is added to the bot’s [`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree") as well.

Note

Exceptions raised inside a [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")’s [`cog_load()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_load "discord.ext.commands.Cog.cog_load") method will be propagated to the caller.

Changed in version 2.0: [`ClientException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientException "discord.ClientException") is raised when a cog with the same name is already loaded.

Changed in version 2.0: `cog` parameter is now positional-only.

Changed in version 2.0: This method is now a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine "(in Python v3.13)").

Parameters

*   **cog** ([`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")) – The cog to register to the bot.
    
*   **override** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    If a previously loaded cog with the same name should be ejected instead of raising an error.
    
    New in version 2.0.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    If the cog is an application command group, then this would be the guild where the cog group would be added to. If not given then it becomes a global command instead.
    
    New in version 2.0.
    
*   **guilds** (List[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    If the cog is an application command group, then this would be the guilds where the cog group would be added to. If not given then it becomes a global command instead. Cannot be mixed with `guild`.
    
    New in version 2.0.
    

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The cog does not inherit from [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog").
    
*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – An error happened during loading.
    
*   [**ClientException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientException "discord.ClientException") – A cog with the same name is already loaded.
    

add_command(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_command "Permalink to this definition")

Adds a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") into the internal list of commands.

This is usually not called, instead the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.command "discord.ext.commands.GroupMixin.command") or [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.group "discord.ext.commands.GroupMixin.group") shortcut decorators are used instead.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to add.

Raises

*   [**CommandRegistrationError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError "discord.ext.commands.CommandRegistrationError") – If the command or its alias is already registered by different command.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the command passed is not a subclass of [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command").
    

add_dynamic_items(_*items_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_dynamic_items "Permalink to this definition")

Registers [`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem") classes for persistent listening.

This method accepts _class types_ rather than instances.

New in version 2.4.

Parameters

***items** (Type[[`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem")]) – The classes of dynamic items to add.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – A class is not a subclass of [`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem").

add_listener(_func_, _/_, _name=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_listener "Permalink to this definition")

The non decorator alternative to [`listen()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.listen "discord.ext.commands.Bot.listen").

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

*   **func** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The function to call.
    
*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the event to listen for. Defaults to `func.__name__`.
    

Example

content_copy

```
async def on_ready(): pass
async def my_message(message): pass

bot.add_listener(on_ready)
bot.add_listener(my_message, 'on_message')
```

add_view(_view_, _*_, _message_id=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_view "Permalink to this definition")

Registers a [`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View") for persistent listening.

This method should be used for when a view is comprised of components that last longer than the lifecycle of the program.

New in version 2.0.

Parameters

*   **view** (Union[[`discord.ui.View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`discord.ui.LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]) – The view to register for dispatching.
    
*   **message_id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The message ID that the view is attached to. This is currently used to refresh the view’s state during message update events. If not given then message update events are not propagated for the view.
    

Raises

*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – A view was not passed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The view is not persistent or is already finished. A persistent view has no timeout and all their components have an explicitly provided custom_id.
    

_property_ allowed_mentions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.allowed_mentions "Permalink to this definition")

The allowed mention configuration.

New in version 1.4.

Type

Optional[[`AllowedMentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions "discord.AllowedMentions")]

_property_ application[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application "Permalink to this definition")

The client’s application info.

This is retrieved on [`login()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.login "discord.Client.login") and is not updated afterwards. This allows populating the application_id without requiring a gateway connection.

This is `None` if accessed before [`login()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.login "discord.Client.login") is called.

New in version 2.0.

Type

Optional[[`AppInfo`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AppInfo "discord.AppInfo")]

_property_ application_flags[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application_flags "Permalink to this definition")

The client’s application flags.

New in version 2.0.

Type

[`ApplicationFlags`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ApplicationFlags "discord.ApplicationFlags")

_property_ application_id[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application_id "Permalink to this definition")

The client’s application ID.

If this is not passed via `__init__` then this is retrieved through the gateway when an event contains the data or after a call to [`login()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.login "discord.Client.login"). Usually after [`on_connect()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.on_connect "discord.on_connect") is called.

New in version 2.0.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_await_ application_info()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application_info "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves the bot’s application information.

Raises

[**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the information failed somehow.

Returns

The bot’s application information.

Return type

[`AppInfo`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AppInfo "discord.AppInfo")

_await_ before_identify_hook(_shard_id_, _*_, _initial=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_identify_hook "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A hook that is called before IDENTIFYing a session. This is useful if you wish to have more control over the synchronization of multiple IDENTIFYing clients.

The default implementation sleeps for 5 seconds.

New in version 1.4.

Parameters

*   **shard_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The shard ID that requested being IDENTIFY’d
    
*   **initial** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether this IDENTIFY is the first initial IDENTIFY.
    

_property_ cached_messages[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.cached_messages "Permalink to this definition")

Read-only list of messages the connected client has cached.

New in version 1.1.

Type

Sequence[[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")]

_await_ change_presence(_*_, _activity=None_, _status=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.change_presence "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Changes the client’s presence.

Example

content_copy

```
game = discord.Game("with the API")
await client.change_presence(status=discord.Status.idle, activity=game)
```

Changed in version 2.0: Removed the `afk` keyword-only parameter.

Changed in version 2.0: This function will now raise [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") instead of `InvalidArgument`.

Parameters

*   **activity** (Optional[[`BaseActivity`](https://discordpy.readthedocs.io/en/stable/api.html#discord.BaseActivity "discord.BaseActivity")]) – The activity being done. `None` if no currently active activity is done.
    
*   **status** (Optional[[`Status`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Status "discord.Status")]) – Indicates what status to change to. If `None`, then [`Status.online`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Status.online "discord.Status.online") is used.
    

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the `activity` parameter is not the proper type.

clear()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.clear "Permalink to this definition")

Clears the internal state of the bot.

After this, the bot can be considered “re-opened”, i.e. [`is_closed()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_closed "discord.ext.commands.Bot.is_closed") and [`is_ready()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_ready "discord.ext.commands.Bot.is_ready") both return `False` along with the bot’s internal cache cleared.

_await_ close()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.close "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Closes the connection to Discord.

_property_ cogs[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.cogs "Permalink to this definition")

A read-only mapping of cog name to cog.

Type

Mapping[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")]

_property_ commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.commands "Permalink to this definition")

A unique set of commands without aliases that are registered.

Type

Set[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

_await_ connect(_*_, _reconnect=True_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.connect "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Creates a websocket connection and lets the websocket listen to messages from Discord. This is a loop that runs the entire event system and miscellaneous aspects of the library. Control is not resumed until the WebSocket connection is terminated.

Parameters

**reconnect** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If we should attempt reconnecting, either due to internet failure or a specific failure on Discord’s part. Certain disconnects that lead to bad state will not be handled (such as invalid sharding payloads or bad tokens).

Raises

*   [**GatewayNotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.GatewayNotFound "discord.GatewayNotFound") – If the gateway to connect to Discord is not found. Usually if this is thrown then there is a Discord API outage.
    
*   [**ConnectionClosed**](https://discordpy.readthedocs.io/en/stable/api.html#discord.ConnectionClosed "discord.ConnectionClosed") – The websocket connection has been terminated.
    

_await_ create_application_emoji(_*_, _name_, _image_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.create_application_emoji "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Create an emoji for the current application.

New in version 2.5.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The emoji name. Must be between 2 and 32 characters long.
    
*   **image** ([`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "(in Python v3.13)")) – The [bytes-like object](https://docs.python.org/3/glossary.html#term-bytes-like-object "(in Python v3.13)") representing the image data to use. Only JPG, PNG and GIF images are supported.
    

Raises

*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Creating the emoji failed.
    

Returns

The emoji that was created.

Return type

[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji")

_await_ create_dm(_user_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.create_dm "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Creates a [`DMChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.DMChannel "discord.DMChannel") with this user.

This should be rarely called, as this is done transparently for most people.

New in version 2.0.

Parameters

**user** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The user to create a DM with.

Returns

The channel that was created.

Return type

[`DMChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.DMChannel "discord.DMChannel")

_await_ create_entitlement(_sku_, _owner_, _owner_type_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.create_entitlement "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Creates a test [`Entitlement`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Entitlement "discord.Entitlement") for the application.

New in version 2.4.

Parameters

*   **sku** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The SKU to create the entitlement for.
    
*   **owner** ([`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")) – The ID of the owner.
    
*   **owner_type** ([`EntitlementOwnerType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.EntitlementOwnerType "discord.EntitlementOwnerType")) – The type of the owner.
    

Raises

*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The SKU or owner could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Creating the entitlement failed.
    

_await_ create_guild(_*_, _name_, _icon=..._, _code=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.create_guild "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Creates a [`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild").

Bot accounts in more than 10 guilds are not allowed to create guilds.

Changed in version 2.0: `name` and `icon` parameters are now keyword-only. The `region` parameter has been removed.

Changed in version 2.0: This function will now raise [`ValueError`](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") instead of `InvalidArgument`.

Deprecated since version 2.6: This function is deprecated and will be removed in a future version.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the guild.
    
*   **icon** (Optional[[`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "(in Python v3.13)")]) – The [bytes-like object](https://docs.python.org/3/glossary.html#term-bytes-like-object "(in Python v3.13)") representing the icon. See [`ClientUser.edit()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientUser.edit "discord.ClientUser.edit") for more details on what is expected.
    
*   **code** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) –
    
    The code for a template to create the guild with.
    
    New in version 1.4.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Guild creation failed.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – Invalid icon image format given. Must be PNG or JPG.
    

Returns

The guild created. This is not the same guild that is added to cache.

Return type

[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")

_await_ delete_invite(_invite_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.delete_invite "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Revokes an [`Invite`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite "discord.Invite"), URL, or ID to an invite.

You must have [`manage_channels`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.manage_channels "discord.Permissions.manage_channels") in the associated guild to do this.

Changed in version 2.0: `invite` parameter is now positional-only.

Parameters

**invite** (Union[[`Invite`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite "discord.Invite"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The invite to revoke.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permissions to revoke invites.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The invite is invalid or expired.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Revoking the invite failed.
    

_property_ emojis[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.emojis "Permalink to this definition")

The emojis that the connected client has.

Type

Sequence[[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji")]

_async for ... in_ entitlements(_*_, _limit=100_, _before=None_, _after=None_, _skus=None_, _user=None_, _guild=None_, _exclude_ended=False_, _exclude_deleted=True_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.entitlements "Permalink to this definition")

Retrieves an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator "(in Python v3.13)") of the [`Entitlement`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Entitlement "discord.Entitlement") that applications has.

New in version 2.4.

Examples

Usage

content_copy

```
async for entitlement in client.entitlements(limit=100):
    print(entitlement.user_id, entitlement.ends_at)
```

Flattening into a list

content_copy

```
entitlements = [entitlement async for entitlement in client.entitlements(limit=100)]
# entitlements is now a list of Entitlement...
```

All parameters are optional.

Parameters

*   **limit** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The number of entitlements to retrieve. If `None`, it retrieves every entitlement for this application. Note, however, that this would make it a slow operation. Defaults to `100`.
    
*   **before** (Optional[Union[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]]) – Retrieve entitlements before this date or entitlement. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
*   **after** (Optional[Union[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]]) – Retrieve entitlements after this date or entitlement. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
*   **skus** (Optional[Sequence[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]]) – A list of SKUs to filter by.
    
*   **user** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The user to filter by.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) – The guild to filter by.
    
*   **exclude_ended** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to exclude ended entitlements. Defaults to `False`.
    
*   **exclude_deleted** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to exclude deleted entitlements. Defaults to `True`.
    
    New in version 2.5.
    

Raises

*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the entitlements failed.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – Both `after` and `before` were provided, as Discord does not support this type of pagination.
    

Yields

[`Entitlement`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Entitlement "discord.Entitlement") – The entitlement with the application.

_property_ extensions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.extensions "Permalink to this definition")

A read-only mapping of extension name to extension.

Type

Mapping[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`types.ModuleType`](https://docs.python.org/3/library/types.html#types.ModuleType "(in Python v3.13)")]

_await_ fetch_application_emoji(_emoji_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_application_emoji "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves an emoji for the current application.

New in version 2.5.

Parameters

**emoji_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The emoji ID to retrieve.

Raises

*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the emoji failed.
    

Returns

The emoji requested.

Return type

[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji")

_await_ fetch_application_emojis()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_application_emojis "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves all emojis for the current application.

New in version 2.5.

Raises

*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the emojis failed.
    

Returns

The list of emojis for the current application.

Return type

List[[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji")]

_await_ fetch_channel(_channel_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_channel "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a [`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel"), [`abc.PrivateChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.PrivateChannel "discord.abc.PrivateChannel"), or [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread") with the specified ID.

Note

This method is an API call. For general usage, consider [`get_channel()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_channel "discord.ext.commands.Bot.get_channel") instead.

New in version 1.2.

Changed in version 2.0: `channel_id` parameter is now positional-only.

Raises

*   [**InvalidData**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InvalidData "discord.InvalidData") – An unknown channel type was received from Discord.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the channel failed.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – Invalid Channel ID.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permission to fetch this channel.
    

Returns

The channel from the ID.

Return type

Union[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel"), [`abc.PrivateChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.PrivateChannel "discord.abc.PrivateChannel"), [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")]

_await_ fetch_entitlement(_entitlement_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_entitlement "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a [`Entitlement`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Entitlement "discord.Entitlement") with the specified ID.

New in version 2.4.

Parameters

**entitlement_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The entitlement’s ID to fetch from.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – An entitlement with this ID does not exist.
    
*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the entitlement failed.
    

Returns

The entitlement you requested.

Return type

[`Entitlement`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Entitlement "discord.Entitlement")

_await_ fetch_guild(_guild_id_, _/_, _*_, _with_counts=True_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_guild "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a [`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild") from an ID.

Note

This method is an API call. For general usage, consider [`get_guild()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_guild "discord.ext.commands.Bot.get_guild") instead.

Changed in version 2.0: `guild_id` parameter is now positional-only.

Parameters

*   **guild_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The guild’s ID to fetch from.
    
*   **with_counts** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to include count information in the guild. This fills the [`Guild.approximate_member_count`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild.approximate_member_count "discord.Guild.approximate_member_count") and [`Guild.approximate_presence_count`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild.approximate_presence_count "discord.Guild.approximate_presence_count") attributes without needing any privileged intents. Defaults to `True`.
    
    New in version 2.0.
    

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The guild doesn’t exist or you got no access to it.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Getting the guild failed.
    

Returns

The guild from the ID.

Return type

[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")

_await_ fetch_guild_preview(_guild_id_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_guild_preview "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a preview of a [`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild") from an ID. If the guild is discoverable, you don’t have to be a member of it.

New in version 2.5.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The guild doesn’t exist, or is not discoverable and you are not in it.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Getting the guild failed.
    

Returns

The guild preview from the ID.

Return type

[`GuildPreview`](https://discordpy.readthedocs.io/en/stable/api.html#discord.GuildPreview "discord.GuildPreview")

_async for ... in_ fetch_guilds(_*_, _limit=200_, _before=None_, _after=None_, _with_counts=True_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_guilds "Permalink to this definition")

Retrieves an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator "(in Python v3.13)") that enables receiving your guilds.

Note

This method is an API call. For general usage, consider [`guilds`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.guilds "discord.ext.commands.Bot.guilds") instead.

Examples

Usage

content_copy

```
async for guild in client.fetch_guilds(limit=150):
    print(guild.name)
```

Flattening into a list

content_copy

```
guilds = [guild async for guild in client.fetch_guilds(limit=150)]
# guilds is now a list of Guild...
```

All parameters are optional.

Parameters

*   **limit** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The number of guilds to retrieve. If `None`, it retrieves every guild you have access to. Note, however, that this would make it a slow operation. Defaults to `200`.
    
    Changed in version 2.0: The default has been changed to 200.
    
*   **before** (Union[[`abc.Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]) – Retrieves guilds before this date or object. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
*   **after** (Union[[`abc.Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]) – Retrieve guilds after this date or object. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
*   **with_counts** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to include count information in the guilds. This fills the [`Guild.approximate_member_count`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild.approximate_member_count "discord.Guild.approximate_member_count") and [`Guild.approximate_presence_count`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild.approximate_presence_count "discord.Guild.approximate_presence_count") attributes without needing any privileged intents. Defaults to `True`.
    
    New in version 2.3.
    

Raises

[**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Getting the guilds failed.

Yields

[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild") – The guild with the guild data parsed.

_await_ fetch_invite(_url_, _*_, _with_counts=True_, _with_expiration=True_, _scheduled_event_id=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_invite "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Gets an [`Invite`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite "discord.Invite") from a discord.gg URL or ID.

Parameters

*   **url** (Union[[`Invite`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite "discord.Invite"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The Discord invite ID or URL (must be a discord.gg URL).
    
*   **with_counts** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to include count information in the invite. This fills the [`Invite.approximate_member_count`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite.approximate_member_count "discord.Invite.approximate_member_count") and [`Invite.approximate_presence_count`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite.approximate_presence_count "discord.Invite.approximate_presence_count") fields.
    
*   **with_expiration** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to include the expiration date of the invite. This fills the [`Invite.expires_at`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite.expires_at "discord.Invite.expires_at") field.
    
    New in version 2.0.
    
    Deprecated since version 2.6: This parameter is deprecated and will be removed in a future version as it is no longer needed to fill the [`Invite.expires_at`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite.expires_at "discord.Invite.expires_at") field.
    
*   **scheduled_event_id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The ID of the scheduled event this invite is for.
    
    Note
    
    It is not possible to provide a url that contains an `event_id` parameter when using this parameter.
    
    New in version 2.0.
    

Raises

*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The url contains an `event_id`, but `scheduled_event_id` has also been provided.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The invite has expired or is invalid.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Getting the invite failed.
    

Returns

The invite from the URL/ID.

Return type

[`Invite`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite "discord.Invite")

_await_ fetch_premium_sticker_pack(_sticker_pack_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_premium_sticker_pack "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a premium sticker pack with the specified ID.

New in version 2.5.

Parameters

**sticker_pack_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The sticker pack’s ID to fetch from.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – A sticker pack with this ID does not exist.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the sticker pack failed.
    

Returns

The retrieved premium sticker pack.

Return type

[`StickerPack`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StickerPack "discord.StickerPack")

_await_ fetch_premium_sticker_packs()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_premium_sticker_packs "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves all available premium sticker packs.

New in version 2.0.

Raises

[**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the sticker packs failed.

Returns

All available premium sticker packs.

Return type

List[[`StickerPack`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StickerPack "discord.StickerPack")]

_await_ fetch_skus()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_skus "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves the bot’s available SKUs.

New in version 2.4.

Raises

*   [**MissingApplicationID**](https://discordpy.readthedocs.io/en/stable/api.html#discord.MissingApplicationID "discord.MissingApplicationID") – The application ID could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the SKUs failed.
    

Returns

The bot’s available SKUs.

Return type

List[[`SKU`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SKU "discord.SKU")]

_await_ fetch_soundboard_default_sounds()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_soundboard_default_sounds "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves all default soundboard sounds.

New in version 2.5.

Raises

[**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the default soundboard sounds failed.

Returns

All default soundboard sounds.

Return type

List[[`SoundboardDefaultSound`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SoundboardDefaultSound "discord.SoundboardDefaultSound")]

_await_ fetch_stage_instance(_channel_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_stage_instance "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Gets a [`StageInstance`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StageInstance "discord.StageInstance") for a stage channel id.

New in version 2.0.

Parameters

**channel_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The stage channel ID.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The stage instance or channel could not be found.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Getting the stage instance failed.
    

Returns

The stage instance from the stage channel ID.

Return type

[`StageInstance`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StageInstance "discord.StageInstance")

_await_ fetch_sticker(_sticker_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_sticker "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a [`Sticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Sticker "discord.Sticker") with the specified ID.

New in version 2.0.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the sticker failed.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – Invalid sticker ID.
    

Returns

The sticker you requested.

Return type

Union[[`StandardSticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StandardSticker "discord.StandardSticker"), [`GuildSticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.GuildSticker "discord.GuildSticker")]

_await_ fetch_template(_code_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_template "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Gets a [`Template`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Template "discord.Template") from a discord.new URL or code.

Parameters

**code** (Union[[`Template`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Template "discord.Template"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The Discord Template Code or URL (must be a discord.new URL).

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The template is invalid.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Getting the template failed.
    

Returns

The template from the URL/code.

Return type

[`Template`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Template "discord.Template")

_await_ fetch_user(_user_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_user "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a [`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User") based on their ID. You do not have to share any guilds with the user to get this information, however many operations do require that you do.

Changed in version 2.0: `user_id` parameter is now positional-only.

Parameters

**user_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The user’s ID to fetch from.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – A user with this ID does not exist.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Fetching the user failed.
    

Returns

The user you requested.

Return type

[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User")

_await_ fetch_webhook(_webhook_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_webhook "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a [`Webhook`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Webhook "discord.Webhook") with the specified ID.

Changed in version 2.0: `webhook_id` parameter is now positional-only.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the webhook failed.
    
*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – Invalid webhook ID.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permission to fetch this webhook.
    

Returns

The webhook you requested.

Return type

[`Webhook`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Webhook "discord.Webhook")

_await_ fetch_widget(_guild_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_widget "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Gets a [`Widget`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Widget "discord.Widget") from a guild ID.

Note

The guild must have the widget enabled to get this information.

Changed in version 2.0: `guild_id` parameter is now positional-only.

Parameters

**guild_id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID of the guild.

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – The widget for this guild is disabled.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the widget failed.
    

Returns

The guild’s widget.

Return type

[`Widget`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Widget "discord.Widget")

_for ... in_ get_all_channels()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_all_channels "Permalink to this definition")

A generator that retrieves every [`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel") the client can ‘access’.

This is equivalent to:

content_copy

```
for guild in client.guilds:
    for channel in guild.channels:
        yield channel
```

Yields

[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel") – A channel the client can ‘access’.

_for ... in_ get_all_members()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_all_members "Permalink to this definition")

Returns a generator with every [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member") the client can see.

This is equivalent to:

content_copy

```
for guild in client.guilds:
    for member in guild.members:
        yield member
```

Yields

[`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member") – A member the client can see.

get_channel(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_channel "Permalink to this definition")

Returns a channel or thread with the given ID.

Changed in version 2.0: `id` parameter is now positional-only.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID to search for.

Returns

The returned channel or `None` if not found.

Return type

Optional[Union[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel"), [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread"), [`abc.PrivateChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.PrivateChannel "discord.abc.PrivateChannel")]]

get_cog(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_cog "Permalink to this definition")

Gets the cog instance requested.

If the cog is not found, `None` is returned instead.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the cog you are requesting. This is equivalent to the name passed via keyword argument in class creation or the class name if unspecified.

Returns

The cog that was requested. If not found, returns `None`.

Return type

Optional[[`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")]

get_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_command "Permalink to this definition")

Get a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to get aliases.

The name could be fully qualified (e.g. `'foo bar'`) will get the subcommand `bar` of the group command `foo`. If a subcommand is not found then `None` is returned just as usual.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to get.

Returns

The command that was requested. If not found, returns `None`.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

_await_ get_context(_origin_, _/_, _*_, _cls=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_context "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Returns the invocation context from the message or interaction.

This is a more low-level counter-part for [`process_commands()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.process_commands "discord.ext.commands.Bot.process_commands") to allow users more fine grained control over the processing.

The returned context is not guaranteed to be a valid invocation context, [`Context.valid`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.valid "discord.ext.commands.Context.valid") must be checked to make sure it is. If the context is not valid then it is not a valid candidate to be invoked under [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "discord.ext.commands.Bot.invoke").

Note

In order for the custom context to be used inside an interaction-based context (such as [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand")) then this method must be overridden to return that class.

Changed in version 2.0: `message` parameter is now positional-only and renamed to `origin`.

Parameters

*   **origin** (Union[[`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message"), [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")]) – The message or interaction to get the invocation context from.
    
*   **cls** – The factory class that will be used to create the context. By default, this is [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context"). Should a custom class be provided, it must be similar enough to [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")'s interface.
    

Returns

The invocation context. The type of this can change via the `cls` parameter.

Return type

[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")

get_emoji(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_emoji "Permalink to this definition")

Returns an emoji with the given ID.

Changed in version 2.0: `id` parameter is now positional-only.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID to search for.

Returns

The custom emoji or `None` if not found.

Return type

Optional[[`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji")]

get_guild(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_guild "Permalink to this definition")

Returns a guild with the given ID.

Changed in version 2.0: `id` parameter is now positional-only.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID to search for.

Returns

The guild or `None` if not found.

Return type

Optional[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

get_partial_messageable(_id_, _*_, _guild_id=None_, _type=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_partial_messageable "Permalink to this definition")

Returns a partial messageable with the given channel ID.

This is useful if you have a channel_id but don’t want to do an API call to send messages to it.

New in version 2.0.

Parameters

*   **id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The channel ID to create a partial messageable for.
    
*   **guild_id** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) –
    
    The optional guild ID to create a partial messageable for.
    
    This is not required to actually send messages, but it does allow the [`jump_url()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialMessageable.jump_url "discord.PartialMessageable.jump_url") and [`guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialMessageable.guild "discord.PartialMessageable.guild") properties to function properly.
    
*   **type** (Optional[[`ChannelType`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ChannelType "discord.ChannelType")]) – The underlying channel type for the partial messageable.
    

Returns

The partial messageable

Return type

[`PartialMessageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialMessageable "discord.PartialMessageable")

_await_ get_prefix(_message_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_prefix "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves the prefix the bot is listening to with the message as a context.

Changed in version 2.0: `message` parameter is now positional-only.

Parameters

**message** ([`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")) – The message context to get the prefix of.

Returns

A list of prefixes or a single prefix that the bot is listening for.

Return type

Union[List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")], [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

get_soundboard_sound(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_soundboard_sound "Permalink to this definition")

Returns a soundboard sound with the given ID.

New in version 2.5.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID to search for.

Returns

The soundboard sound or `None` if not found.

Return type

Optional[[`SoundboardSound`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SoundboardSound "discord.SoundboardSound")]

get_stage_instance(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_stage_instance "Permalink to this definition")

Returns a stage instance with the given stage channel ID.

New in version 2.0.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID to search for.

Returns

The stage instance or `None` if not found.

Return type

Optional[[`StageInstance`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StageInstance "discord.StageInstance")]

get_sticker(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_sticker "Permalink to this definition")

Returns a guild sticker with the given ID.

New in version 2.0.

Returns

The sticker or `None` if not found.

Return type

Optional[[`GuildSticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.GuildSticker "discord.GuildSticker")]

get_user(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_user "Permalink to this definition")

Returns a user with the given ID.

Changed in version 2.0: `id` parameter is now positional-only.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The ID to search for.

Returns

The user or `None` if not found.

Return type

Optional[[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User")]

_property_ guilds[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.guilds "Permalink to this definition")

The guilds that the connected client is a member of.

Type

Sequence[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

_property_ intents[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.intents "Permalink to this definition")

The intents configured for this connection.

New in version 1.5.

Type

[`Intents`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Intents "discord.Intents")

_await_ invoke(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Invokes the command given under the invocation context and handles all the internal event dispatch mechanisms.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to invoke.

is_closed()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_closed "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Indicates if the websocket connection is closed.

_await_ is_owner(_user_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_owner "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Checks if a [`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User") or [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member") is the owner of this bot.

If an [`owner_id`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.owner_id "discord.ext.commands.Bot.owner_id") is not set, it is fetched automatically through the use of [`application_info()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.application_info "discord.ext.commands.Bot.application_info").

Changed in version 1.3: The function also checks if the application is team-owned if [`owner_ids`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.owner_ids "discord.ext.commands.Bot.owner_ids") is not set.

Changed in version 2.0: `user` parameter is now positional-only.

Changed in version 2.4: This function now respects the team member roles if the bot is team-owned. In order to be considered an owner, they must be either an admin or a developer.

Parameters

**user** ([`abc.User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.User "discord.abc.User")) – The user to check for.

Returns

Whether the user is the owner.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

is_ready()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_ready "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Specifies if the client’s internal cache is ready for use.

is_ws_ratelimited()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_ws_ratelimited "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Whether the websocket is currently rate limited.

This can be useful to know when deciding whether you should query members using HTTP or via the gateway.

New in version 1.6.

_property_ latency[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.latency "Permalink to this definition")

Measures latency between a HEARTBEAT and a HEARTBEAT_ACK in seconds.

This could be referred to as the Discord WebSocket protocol latency.

Type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

_await_ load_extension(_name_, _*_, _package=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.load_extension "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Loads an extension.

An extension is a python module that contains commands, cogs, or listeners.

An extension must have a global function, `setup` defined as the entry point on what to do when the extension is loaded. This entry point must have a single argument, the `bot`.

Changed in version 2.0: This method is now a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine "(in Python v3.13)").

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The extension name to load. It must be dot separated like regular Python imports if accessing a sub-module. e.g. `foo.test` if you want to import `foo/test.py`.
    
*   **package** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) –
    
    The package name to resolve relative imports with. This is required when loading an extension using a relative path, e.g `.foo.test`. Defaults to `None`.
    
    New in version 1.7.
    

Raises

*   [**ExtensionNotFound**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotFound "discord.ext.commands.ExtensionNotFound") – The extension could not be imported. This is also raised if the name of the extension could not be resolved using the provided `package` parameter.
    
*   [**ExtensionAlreadyLoaded**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionAlreadyLoaded "discord.ext.commands.ExtensionAlreadyLoaded") – The extension is already loaded.
    
*   [**NoEntryPointError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoEntryPointError "discord.ext.commands.NoEntryPointError") – The extension does not have a setup function.
    
*   [**ExtensionFailed**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionFailed "discord.ext.commands.ExtensionFailed") – The extension or its setup function had an execution error.
    

_await_ login(_token_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.login "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Logs in the client with the specified credentials and calls the [`setup_hook()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.setup_hook "discord.ext.commands.Bot.setup_hook").

Parameters

**token** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The authentication token. Do not prefix this token with anything as the library will do it for you.

Raises

*   [**LoginFailure**](https://discordpy.readthedocs.io/en/stable/api.html#discord.LoginFailure "discord.LoginFailure") – The wrong credentials are passed.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – An unknown HTTP related error occurred, usually when it isn’t 200 or the known incorrect credentials passing status code.
    

_await_ on_command_error(_context_, _exception_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.on_command_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The default command error handler provided by the bot.

By default this logs to the library logger, however it could be overridden to have a different implementation.

This only fires if you do not specify any listeners for command error.

Changed in version 2.0: `context` and `exception` parameters are now positional-only. Instead of writing to `sys.stderr` this now uses the library logger.

_await_ on_error(_event_method_, _/_, _*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.on_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The default error handler provided by the client.

By default this logs to the library logger however it could be overridden to have a different implementation. Check [`on_error()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.on_error "discord.on_error") for more details.

Changed in version 2.0: `event_method` parameter is now positional-only and instead of writing to `sys.stderr` it logs instead.

_property_ persistent_views[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.persistent_views "Permalink to this definition")

A sequence of persistent views added to the client.

New in version 2.0.

Type

Sequence[Union[[`View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]]

_property_ private_channels[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.private_channels "Permalink to this definition")

The private channels that the connected client is participating on.

Note

This returns only up to 128 most recent private channels due to an internal working on how Discord deals with private channels.

Type

Sequence[[`abc.PrivateChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.PrivateChannel "discord.abc.PrivateChannel")]

_await_ process_commands(_message_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.process_commands "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

This function processes the commands that have been registered to the bot and other groups. Without this coroutine, none of the commands will be triggered.

By default, this coroutine is called inside the [`on_message()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.on_message "discord.on_message") event. If you choose to override the [`on_message()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.on_message "discord.on_message") event, then you should invoke this coroutine as well.

This is built using other low level tools, and is equivalent to a call to [`get_context()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_context "discord.ext.commands.Bot.get_context") followed by a call to [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "discord.ext.commands.Bot.invoke").

This also checks if the message’s author is a bot and doesn’t call [`get_context()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.get_context "discord.ext.commands.Bot.get_context") or [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.invoke "discord.ext.commands.Bot.invoke") if so.

Changed in version 2.0: `message` parameter is now positional-only.

Parameters

**message** ([`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")) – The message to process commands for.

_await_ reload_extension(_name_, _*_, _package=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.reload_extension "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Atomically reloads an extension.

This replaces the extension with the same extension, only refreshed. This is equivalent to a [`unload_extension()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.unload_extension "discord.ext.commands.Bot.unload_extension") followed by a [`load_extension()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.load_extension "discord.ext.commands.Bot.load_extension") except done in an atomic way. That is, if an operation fails mid-reload then the bot will roll-back to the prior working state.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The extension name to reload. It must be dot separated like regular Python imports if accessing a sub-module. e.g. `foo.test` if you want to import `foo/test.py`.
    
*   **package** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) –
    
    The package name to resolve relative imports with. This is required when reloading an extension using a relative path, e.g `.foo.test`. Defaults to `None`.
    
    New in version 1.7.
    

Raises

*   [**ExtensionNotLoaded**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotLoaded "discord.ext.commands.ExtensionNotLoaded") – The extension was not loaded.
    
*   [**ExtensionNotFound**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotFound "discord.ext.commands.ExtensionNotFound") – The extension could not be imported. This is also raised if the name of the extension could not be resolved using the provided `package` parameter.
    
*   [**NoEntryPointError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoEntryPointError "discord.ext.commands.NoEntryPointError") – The extension does not have a setup function.
    
*   [**ExtensionFailed**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionFailed "discord.ext.commands.ExtensionFailed") – The extension setup function had an execution error.
    

remove_check(_func_, _/_, _*_, _call_once=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.remove_check "Permalink to this definition")

Removes a global check from the bot.

This function is idempotent and will not raise an exception if the function is not in the global checks.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

*   **func** – The function to remove from the global checks.
    
*   **call_once** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If the function was added with `call_once=True` in the [`Bot.add_check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.add_check "discord.ext.commands.Bot.add_check") call or using [`check_once()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check_once "discord.ext.commands.Bot.check_once").
    

_await_ remove_cog(_name_, _/_, _*_, _guild=..._, _guilds=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.remove_cog "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Removes a cog from the bot and returns it.

All registered commands and event listeners that the cog has registered will be removed as well.

If no cog is found then this method has no effect.

Changed in version 2.0: `name` parameter is now positional-only.

Changed in version 2.0: This method is now a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine "(in Python v3.13)").

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the cog to remove.
    
*   **guild** (Optional[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    If the cog is an application command group, then this would be the guild where the cog group would be removed from. If not given then a global command is removed instead instead.
    
    New in version 2.0.
    
*   **guilds** (List[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]) –
    
    If the cog is an application command group, then this would be the guilds where the cog group would be removed from. If not given then a global command is removed instead instead. Cannot be mixed with `guild`.
    
    New in version 2.0.
    

Returns

The cog that was removed. `None` if not found.

Return type

Optional[[`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")]

remove_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.remove_command "Permalink to this definition")

Remove a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to remove aliases.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to remove.

Returns

The command that was removed. If the name is not valid then `None` is returned instead.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

remove_dynamic_items(_*items_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.remove_dynamic_items "Permalink to this definition")

Removes [`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem") classes from persistent listening.

This method accepts _class types_ rather than instances.

New in version 2.4.

Parameters

***items** (Type[[`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem")]) – The classes of dynamic items to remove.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – A class is not a subclass of [`DynamicItem`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.DynamicItem "discord.ui.DynamicItem").

remove_listener(_func_, _/_, _name=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.remove_listener "Permalink to this definition")

Removes a listener from the pool of listeners.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

*   **func** – The function that was used as a listener to remove.
    
*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the event we want to remove. Defaults to `func.__name__`.
    

run(_token_, _*_, _reconnect=True_, _log_handler=..._, _log_formatter=..._, _log_level=..._, _root_logger=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.run "Permalink to this definition")

A blocking call that abstracts away the event loop initialisation from you.

If you want more control over the event loop then this function should not be used. Use [`start()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.start "discord.ext.commands.Bot.start") coroutine or [`connect()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.connect "discord.ext.commands.Bot.connect") + [`login()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.login "discord.ext.commands.Bot.login").

This function also sets up the logging library to make it easier for beginners to know what is going on with the library. For more advanced users, this can be disabled by passing `None` to the `log_handler` parameter.

Warning

This function must be the last function to call due to the fact that it is blocking. That means that registration of events or anything being called after this function call will not execute until it returns.

Parameters

*   **token** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The authentication token. Do not prefix this token with anything as the library will do it for you.
    
*   **reconnect** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If we should attempt reconnecting, either due to internet failure or a specific failure on Discord’s part. Certain disconnects that lead to bad state will not be handled (such as invalid sharding payloads or bad tokens).
    
*   **log_handler** (Optional[[`logging.Handler`](https://docs.python.org/3/library/logging.html#logging.Handler "(in Python v3.13)")]) –
    
    The log handler to use for the library’s logger. If this is `None` then the library will not set up anything logging related. Logging will still work if `None` is passed, though it is your responsibility to set it up.
    
    The default log handler if not provided is [`logging.StreamHandler`](https://docs.python.org/3/library/logging.handlers.html#logging.StreamHandler "(in Python v3.13)").
    
    New in version 2.0.
    
*   **log_formatter** ([`logging.Formatter`](https://docs.python.org/3/library/logging.html#logging.Formatter "(in Python v3.13)")) –
    
    The formatter to use with the given log handler. If not provided then it defaults to a colour based logging formatter (if available).
    
    New in version 2.0.
    
*   **log_level** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) –
    
    The default log level for the library’s logger. This is only applied if the `log_handler` parameter is not `None`. Defaults to `logging.INFO`.
    
    New in version 2.0.
    
*   **root_logger** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to set up the root logger rather than the library logger. By default, only the library logger (`'discord'`) is set up. If this is set to `True` then the root logger is set up as well.
    
    Defaults to `False`.
    
    New in version 2.0.
    

_await_ setup_hook()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.setup_hook "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A coroutine to be called to setup the bot, by default this is blank.

To perform asynchronous setup after the bot is logged in but before it has connected to the Websocket, overwrite this coroutine.

This is only called once, in [`login()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.login "discord.ext.commands.Bot.login"), and will be called before any events are dispatched, making it a better solution than doing such setup in the [`on_ready()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.on_ready "discord.on_ready") event.

Warning

Since this is called _before_ the websocket connection is made therefore anything that waits for the websocket will deadlock, this includes things like [`wait_for()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.wait_for "discord.ext.commands.Bot.wait_for") and [`wait_until_ready()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.wait_until_ready "discord.ext.commands.Bot.wait_until_ready").

New in version 2.0.

_property_ soundboard_sounds[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.soundboard_sounds "Permalink to this definition")

The soundboard sounds that the connected client has.

New in version 2.5.

Type

List[[`SoundboardSound`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SoundboardSound "discord.SoundboardSound")]

_await_ start(_token_, _*_, _reconnect=True_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.start "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A shorthand coroutine for [`login()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.login "discord.ext.commands.Bot.login") + [`connect()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.connect "discord.ext.commands.Bot.connect").

Parameters

*   **token** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The authentication token. Do not prefix this token with anything as the library will do it for you.
    
*   **reconnect** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – If we should attempt reconnecting, either due to internet failure or a specific failure on Discord’s part. Certain disconnects that lead to bad state will not be handled (such as invalid sharding payloads or bad tokens).
    

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – An unexpected keyword argument was received.

_property_ status[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.status "Permalink to this definition")

[`Status`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Status "discord.Status"): The status being used upon logging on to Discord.

_property_ stickers[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.stickers "Permalink to this definition")

The stickers that the connected client has.

New in version 2.0.

Type

Sequence[[`GuildSticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.GuildSticker "discord.GuildSticker")]

_property_ tree[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.tree "Permalink to this definition")

The command tree responsible for handling the application commands in this bot.

New in version 2.0.

Type

[`CommandTree`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree "discord.app_commands.CommandTree")

_await_ unload_extension(_name_, _*_, _package=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.unload_extension "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Unloads an extension.

When the extension is unloaded, all commands, listeners, and cogs are removed from the bot and the module is un-imported.

The extension can provide an optional global function, `teardown`, to do miscellaneous clean-up if necessary. This function takes a single parameter, the `bot`, similar to `setup` from [`load_extension()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.load_extension "discord.ext.commands.Bot.load_extension").

Changed in version 2.0: This method is now a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine "(in Python v3.13)").

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The extension name to unload. It must be dot separated like regular Python imports if accessing a sub-module. e.g. `foo.test` if you want to import `foo/test.py`.
    
*   **package** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) –
    
    The package name to resolve relative imports with. This is required when unloading an extension using a relative path, e.g `.foo.test`. Defaults to `None`.
    
    New in version 1.7.
    

Raises

*   [**ExtensionNotFound**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotFound "discord.ext.commands.ExtensionNotFound") – The name of the extension could not be resolved using the provided `package` parameter.
    
*   [**ExtensionNotLoaded**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotLoaded "discord.ext.commands.ExtensionNotLoaded") – The extension was not loaded.
    

_property_ user[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.user "Permalink to this definition")

Represents the connected client. `None` if not logged in.

Type

Optional[[`ClientUser`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientUser "discord.ClientUser")]

_property_ users[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.users "Permalink to this definition")

Returns a list of all the users the bot can see.

Type

List[[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User")]

_property_ voice_clients[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.voice_clients "Permalink to this definition")

Represents a list of voice connections.

These are usually [`VoiceClient`](https://discordpy.readthedocs.io/en/stable/api.html#discord.VoiceClient "discord.VoiceClient") instances.

Type

List[[`VoiceProtocol`](https://discordpy.readthedocs.io/en/stable/api.html#discord.VoiceProtocol "discord.VoiceProtocol")]

wait_for(_event_, _/_, _*_, _check=None_, _timeout=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.wait_for "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Waits for a WebSocket event to be dispatched.

This could be used to wait for a user to reply to a message, or to react to a message, or to edit a message in a self-contained way.

The `timeout` parameter is passed onto [`asyncio.wait_for()`](https://docs.python.org/3/library/asyncio-task.html#asyncio.wait_for "(in Python v3.13)"). By default, it does not timeout. Note that this does propagate the [`asyncio.TimeoutError`](https://docs.python.org/3/library/asyncio-exceptions.html#asyncio.TimeoutError "(in Python v3.13)") for you in case of timeout and is provided for ease of use.

In case the event returns multiple arguments, a [`tuple`](https://docs.python.org/3/library/stdtypes.html#tuple "(in Python v3.13)") containing those arguments is returned instead. Please check the [documentation](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-events) for a list of events and their parameters.

This function returns the **first event that meets the requirements**.

Examples

Waiting for a user reply:

content_copy

```
@client.event
async def on_message(message):
    if message.content.startswith('$greet'):
        channel = message.channel
        await channel.send('Say hello!')

        def check(m):
            return m.content == 'hello' and m.channel == channel

        msg = await client.wait_for('message', check=check)
        await channel.send(f'Hello {msg.author}!')
```

Waiting for a thumbs up reaction from the message author:

content_copy

```
@client.event
async def on_message(message):
    if message.content.startswith('$thumb'):
        channel = message.channel
        await channel.send('Send me that 👍 reaction, mate')

        def check(reaction, user):
            return user == message.author and str(reaction.emoji) == '👍'

        try:
            reaction, user = await client.wait_for('reaction_add', timeout=60.0, check=check)
        except asyncio.TimeoutError:
            await channel.send('👎')
        else:
            await channel.send('👍')
```

Changed in version 2.0: `event` parameter is now positional-only.

Parameters

*   **event** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The event name, similar to the [event reference](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-events), but without the `on_` prefix, to wait for.
    
*   **check** (Optional[Callable[…, [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]]) – A predicate to check what to wait for. The arguments must meet the parameters of the event being waited for.
    
*   **timeout** (Optional[[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]) – The number of seconds to wait before timing out and raising [`asyncio.TimeoutError`](https://docs.python.org/3/library/asyncio-exceptions.html#asyncio.TimeoutError "(in Python v3.13)").
    

Raises

[**asyncio.TimeoutError**](https://docs.python.org/3/library/asyncio-exceptions.html#asyncio.TimeoutError "(in Python v3.13)") – If a timeout is provided and it was reached.

Returns

Returns no arguments, a single argument, or a [`tuple`](https://docs.python.org/3/library/stdtypes.html#tuple "(in Python v3.13)") of multiple arguments that mirrors the parameters passed in the [event reference](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-events).

Return type

Any

_await_ wait_until_ready()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.wait_until_ready "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Waits until the client’s internal cache is all ready.

Warning

Calling this inside [`setup_hook()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.setup_hook "discord.ext.commands.Bot.setup_hook") can lead to a deadlock.

_for ... in_ walk_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.walk_commands "Permalink to this definition")

An iterator that recursively walks through all commands and subcommands.

Changed in version 1.4: Duplicates due to aliases are no longer returned

Yields

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")] – A command or group from the internal list of commands.

### AutoShardedBot[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#autoshardedbot "Permalink to this headline")

_class_ discord.ext.commands.AutoShardedBot(_command_prefix_, _*_, _help_command=<default-help-command>_, _tree_cls=<class 'discord.app_commands.tree.CommandTree'>_, _description=None_, _allowed_contexts=..._, _allowed_installs=..._, _intents_, _**options_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.AutoShardedBot "Permalink to this definition")

This is similar to [`Bot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot "discord.ext.commands.Bot") except that it is inherited from [`discord.AutoShardedClient`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AutoShardedClient "discord.AutoShardedClient") instead.

async with x

Asynchronously initialises the bot and automatically cleans.

New in version 2.0.

## Prefix Helpers[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#prefix-helpers "Permalink to this headline")

discord.ext.commands.when_mentioned(_bot_, _msg_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.when_mentioned "Permalink to this definition")

A callable that implements a command prefix equivalent to being mentioned.

These are meant to be passed into the [`Bot.command_prefix`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.command_prefix "discord.ext.commands.Bot.command_prefix") attribute.

Changed in version 2.0: `bot` and `msg` parameters are now positional-only.

discord.ext.commands.when_mentioned_or(_*prefixes_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.when_mentioned_or "Permalink to this definition")

A callable that implements when mentioned or other prefixes provided.

These are meant to be passed into the [`Bot.command_prefix`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.command_prefix "discord.ext.commands.Bot.command_prefix") attribute.

Example

content_copy

```
bot = commands.Bot(command_prefix=commands.when_mentioned_or('!'))
```

Note

This callable returns another callable, so if this is done inside a custom callable, you must call the returned callable, for example:

content_copy

```
async def get_prefix(bot, message):
    extras = await prefixes_for(message.guild) # returns a list
    return commands.when_mentioned_or(*extras)(bot, message)
```

## Event Reference[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#event-reference "Permalink to this headline")

These events function similar to [the regular events](https://discordpy.readthedocs.io/en/stable/api.html#discord-api-events), except they are custom to the command extension module.

discord.ext.commands.on_command_error(_ctx_, _error_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "Permalink to this definition")

An error handler that is called when an error is raised inside a command either through user input error, check failure, or an error in your own code.

A default one is provided ([`Bot.on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.on_command_error "discord.ext.commands.Bot.on_command_error")).

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.
    
*   **error** ([`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived) – The error that was raised.
    

discord.ext.commands.on_command(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command "Permalink to this definition")

An event that is called when a command is found and is about to be invoked.

This event is called regardless of whether the command itself succeeds via error or completes.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.

discord.ext.commands.on_command_completion(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_completion "Permalink to this definition")

An event that is called when a command has completed its invocation.

This event is called only if the command succeeded, i.e. all checks have passed and the user input it correctly.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.

## Commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#commands "Permalink to this headline")

### Decorators[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#decorators "Permalink to this headline")

@discord.ext.commands.command(_name=..._, _cls=..._, _**attrs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "Permalink to this definition")

A decorator that transforms a function into a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") or if called with [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.group "discord.ext.commands.group"), [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group").

By default the `help` attribute is received automatically from the docstring of the function and is cleaned up with the use of `inspect.cleandoc`. If the docstring is `bytes`, then it is decoded into [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)") using utf-8 encoding.

All checks added using the [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") & co. decorators are added into the function. There is no way to supply your own checks through this decorator.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name to create the command with. By default this uses the function name unchanged.
    
*   **cls** – The class to construct with. By default this is [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"). You usually do not change this.
    
*   **attrs** – Keyword arguments to pass into the construction of the class denoted by `cls`.
    

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the function is not a coroutine or is already a command.

@discord.ext.commands.group(_name=..._, _cls=..._, _**attrs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.group "Permalink to this definition")

A decorator that transforms a function into a [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group").

This is similar to the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") decorator but the `cls` parameter is set to [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group") by default.

Changed in version 1.1: The `cls` parameter can now be passed.

@discord.ext.commands.hybrid_command(_name=..._, _*_, _with_app_command=True_, _**attrs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.hybrid_command "Permalink to this definition")

A decorator that transforms a function into a [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand").

A hybrid command is one that functions both as a regular [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") and one that is also a [`app_commands.Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command").

The callback being attached to the command must be representable as an application command callback. Converters are silently converted into a [`Transformer`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Transformer "discord.app_commands.Transformer") with a [`discord.AppCommandOptionType.string`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.AppCommandOptionType.string "discord.AppCommandOptionType.string") type.

Checks and error handlers are dispatched and called as-if they were commands similar to [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"). This means that they take [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") as a parameter rather than [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction").

All checks added using the [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") & co. decorators are added into the function. There is no way to supply your own checks through this decorator.

New in version 2.0.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name to create the command with. By default this uses the function name unchanged.
    
*   **with_app_command** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to register the command also as an application command.
    
*   ****attrs** – Keyword arguments to pass into the construction of the hybrid command.
    

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the function is not a coroutine or is already a command.

@discord.ext.commands.hybrid_group(_name=..._, _*_, _with_app_command=True_, _**attrs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.hybrid_group "Permalink to this definition")

A decorator that transforms a function into a [`HybridGroup`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup "discord.ext.commands.HybridGroup").

This is similar to the [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.group "discord.ext.commands.group") decorator except it creates a hybrid group instead.

Parameters

*   **name** (Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]) – The name to create the group with. By default this uses the function name unchanged.
    
*   **with_app_command** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to register the command also as an application command.
    

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the function is not a coroutine or is already a command.

### Command[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#command "Permalink to this headline")

_class_ discord.ext.commands.Command(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "Permalink to this definition")

A class that implements the protocol for a bot text command.

These are not created manually, instead they are created via the decorator or functional interface.

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.name "Permalink to this definition")

The name of the command.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

callback[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.callback "Permalink to this definition")

The coroutine that is executed when the command is called.

Type

[coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")

help[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.help "Permalink to this definition")

The long help text for the command.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

brief[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.brief "Permalink to this definition")

The short help text for the command.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

usage[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.usage "Permalink to this definition")

A replacement for arguments in the default help text.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

aliases[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.aliases "Permalink to this definition")

The list of aliases the command can be invoked under.

Type

Union[List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")], Tuple[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]]

enabled[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.enabled "Permalink to this definition")

A boolean that indicates if the command is currently enabled. If the command is invoked while it is disabled, then [`DisabledCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DisabledCommand "discord.ext.commands.DisabledCommand") is raised to the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event. Defaults to `True`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

parent[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.parent "Permalink to this definition")

The parent group that this command belongs to. `None` if there isn’t one.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

cog[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.cog "Permalink to this definition")

The cog that this command belongs to. `None` if there isn’t one.

Type

Optional[[`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")]

checks[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "Permalink to this definition")

A list of predicates that verifies if the command could be executed with the given [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") as the sole parameter. If an exception is necessary to be thrown to signal failure, then one inherited from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") should be used. Note that if the checks fail then [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure") exception is raised to the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event.

Type

List[Callable[[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")], [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]]

description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.description "Permalink to this definition")

The message prefixed into the default help command.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

hidden[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.hidden "Permalink to this definition")

If `True`, the default help command does not show this in the help output.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

rest_is_raw[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.rest_is_raw "Permalink to this definition")

If `False` and a keyword-only argument is provided then the keyword only argument is stripped and handled as if it was a regular argument that handles [`MissingRequiredArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredArgument "discord.ext.commands.MissingRequiredArgument") and default values in a regular matter rather than passing the rest completely raw. If `True` then the keyword-only argument will pass in the rest of the arguments in a completely raw matter. Defaults to `False`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

invoked_subcommand[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.invoked_subcommand "Permalink to this definition")

The subcommand that was invoked, if any.

Type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

require_var_positional[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.require_var_positional "Permalink to this definition")

If `True` and a variadic positional argument is specified, requires the user to specify at least one argument. Defaults to `False`.

New in version 1.5.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

ignore_extra[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.ignore_extra "Permalink to this definition")

If `True`, ignores extraneous strings passed to a command if all its requirements are met (e.g. `?foo a b c` when only expecting `a` and `b`). Otherwise [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") and local error handlers are called with [`TooManyArguments`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TooManyArguments "discord.ext.commands.TooManyArguments"). Defaults to `True`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

cooldown_after_parsing[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.cooldown_after_parsing "Permalink to this definition")

If `True`, cooldown processing is done after argument parsing, which calls converters. If `False` then cooldown processing is done first and then the converters are called second. Defaults to `False`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

extras[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.extras "Permalink to this definition")

A dict of user provided extras to attach to the Command.

Note

This object may be copied by the library.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

New in version 2.0.

@after_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.after_invoke "Permalink to this definition")

A decorator that registers a coroutine as a post-invoke hook.

A post-invoke hook is called directly after the command is called. This makes it a useful function to clean-up database connections or any type of clean up required.

This post-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.after_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.after_invoke "discord.ext.commands.Bot.after_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the post-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@before_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.before_invoke "Permalink to this definition")

A decorator that registers a coroutine as a pre-invoke hook.

A pre-invoke hook is called directly before the command is called. This makes it a useful function to set up database connections or any type of set up required.

This pre-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "discord.ext.commands.Bot.before_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the pre-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@error[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

A local error handler is an [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event limited to a single command. However, the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") is still invoked afterwards as the catch-all.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

add_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.add_check "Permalink to this definition")

Adds a check to the command.

This is the non-decorator interface to [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check").

New in version 1.3.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function that will be used as a check.

remove_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.remove_check "Permalink to this definition")

Removes a check from the command.

This function is idempotent and will not raise an exception if the function is not in the command’s checks.

New in version 1.3.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function to remove from the checks.

update(_**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.update "Permalink to this definition")

Updates [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") instance with updated attribute.

This works similarly to the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") decorator in terms of parameters in that they are passed to the [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") or subclass constructors, sans the name and callback.

_await_ __call__(_context_, _/_, _*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.__call__ "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Calls the internal callback that the command holds.

Note

This bypasses all mechanisms – including checks, converters, invoke hooks, cooldowns, etc. You must take care to pass the proper arguments and types to this function.

New in version 1.3.

Changed in version 2.0: `context` parameter is now positional-only.

copy()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.copy "Permalink to this definition")

Creates a copy of this command.

Returns

A new instance of this command.

Return type

[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")

_property_ clean_params[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.clean_params "Permalink to this definition")

Dict[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")]: Retrieves the parameter dictionary without the context or self parameters.

Useful for inspecting signature.

_property_ cooldown[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.cooldown "Permalink to this definition")

The cooldown of a command when invoked or `None` if the command doesn’t have a registered cooldown.

New in version 2.0.

Type

Optional[[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")]

_property_ full_parent_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.full_parent_name "Permalink to this definition")

Retrieves the fully qualified parent command name.

This the base command name required to execute it. For example, in `?one two three` the parent name would be `one two`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ parents[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.parents "Permalink to this definition")

Retrieves the parents of this command.

If the command has no parents then it returns an empty [`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)").

For example in commands `?a b c test`, the parents are `[c, b, a]`.

New in version 1.1.

Type

List[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ root_parent[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.root_parent "Permalink to this definition")

Retrieves the root parent of this command.

If the command has no parents then it returns `None`.

For example in commands `?a b c test`, the root parent is `a`.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.qualified_name "Permalink to this definition")

Retrieves the fully qualified command name.

This is the full parent name with the command name as well. For example, in `?one two three` the qualified name would be `one two three`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

is_on_cooldown(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.is_on_cooldown "Permalink to this definition")

Checks whether the command is currently on cooldown.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to use when checking the commands cooldown status.

Returns

A boolean indicating if the command is on cooldown.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

reset_cooldown(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.reset_cooldown "Permalink to this definition")

Resets the cooldown on this command.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to reset the cooldown under.

get_cooldown_retry_after(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.get_cooldown_retry_after "Permalink to this definition")

Retrieves the amount of seconds before this command can be tried again.

New in version 1.4.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to retrieve the cooldown from.

Returns

The amount of time left on this command’s cooldown in seconds. If this is `0.0` then the command isn’t on cooldown.

Return type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

has_error_handler()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.has_error_handler "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks whether the command has an error handler registered.

New in version 1.7.

_property_ cog_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.cog_name "Permalink to this definition")

The name of the cog this command belongs to, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ short_doc[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.short_doc "Permalink to this definition")

Gets the “short” documentation of a command.

By default, this is the [`brief`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.brief "discord.ext.commands.Command.brief") attribute. If that lookup leads to an empty string then the first line of the [`help`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.help "discord.ext.commands.Command.help") attribute is used instead.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ signature[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.signature "Permalink to this definition")

Returns a POSIX-like signature useful for help command output.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_await_ can_run(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.can_run "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Checks if the command can be executed by checking all the predicates inside the [`checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") attribute. This also checks whether the command is disabled.

Changed in version 1.3: Checks whether the command is disabled or not

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The ctx of the command currently being invoked.

Raises

[**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – Any command error that was raised during a check call will be propagated by this function.

Returns

A boolean indicating if the command can be invoked.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### Group[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#group "Permalink to this headline")

_class_ discord.ext.commands.Group(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "Permalink to this definition")

A class that implements a grouping protocol for commands to be executed as subcommands.

This class is a subclass of [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") and thus all options valid in [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") are valid in here as well.

invoke_without_command[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.invoke_without_command "Permalink to this definition")

Indicates if the group callback should begin parsing and invocation only if no subcommand was found. Useful for making it an error handling function to tell the user that no subcommand was found or to have different functionality in case no subcommand was found. If this is `False`, then the group callback will always be invoked first. This means that the checks and the parsing dictated by its parameters will be executed. Defaults to `False`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

case_insensitive[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.case_insensitive "Permalink to this definition")

Indicates if the group’s commands should be case insensitive. Defaults to `False`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

@after_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.after_invoke "Permalink to this definition")

A decorator that registers a coroutine as a post-invoke hook.

A post-invoke hook is called directly after the command is called. This makes it a useful function to clean-up database connections or any type of clean up required.

This post-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.after_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.after_invoke "discord.ext.commands.Bot.after_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the post-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@before_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.before_invoke "Permalink to this definition")

A decorator that registers a coroutine as a pre-invoke hook.

A pre-invoke hook is called directly before the command is called. This makes it a useful function to set up database connections or any type of set up required.

This pre-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "discord.ext.commands.Bot.before_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the pre-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@command(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.command "Permalink to this definition")

A shortcut decorator that invokes [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Command, adds it to the bot, then returns it.

Return type

Callable[…, [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

@error[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

A local error handler is an [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event limited to a single command. However, the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") is still invoked afterwards as the catch-all.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@group(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.group "Permalink to this definition")

A shortcut decorator that invokes [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.group "discord.ext.commands.group") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Group, adds it to the bot, then returns it.

Return type

Callable[…, [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

copy()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.copy "Permalink to this definition")

Creates a copy of this [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group").

Returns

A new instance of this group.

Return type

[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")

add_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.add_check "Permalink to this definition")

Adds a check to the command.

This is the non-decorator interface to [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check").

New in version 1.3.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function that will be used as a check.

add_command(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.add_command "Permalink to this definition")

Adds a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") into the internal list of commands.

This is usually not called, instead the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.command "discord.ext.commands.GroupMixin.command") or [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.group "discord.ext.commands.GroupMixin.group") shortcut decorators are used instead.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to add.

Raises

*   [**CommandRegistrationError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError "discord.ext.commands.CommandRegistrationError") – If the command or its alias is already registered by different command.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the command passed is not a subclass of [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command").
    

_await_ can_run(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.can_run "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Checks if the command can be executed by checking all the predicates inside the [`checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") attribute. This also checks whether the command is disabled.

Changed in version 1.3: Checks whether the command is disabled or not

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The ctx of the command currently being invoked.

Raises

[**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – Any command error that was raised during a check call will be propagated by this function.

Returns

A boolean indicating if the command can be invoked.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ clean_params[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.clean_params "Permalink to this definition")

Dict[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")]: Retrieves the parameter dictionary without the context or self parameters.

Useful for inspecting signature.

_property_ cog_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.cog_name "Permalink to this definition")

The name of the cog this command belongs to, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.commands "Permalink to this definition")

A unique set of commands without aliases that are registered.

Type

Set[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

_property_ cooldown[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.cooldown "Permalink to this definition")

The cooldown of a command when invoked or `None` if the command doesn’t have a registered cooldown.

New in version 2.0.

Type

Optional[[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")]

_property_ full_parent_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.full_parent_name "Permalink to this definition")

Retrieves the fully qualified parent command name.

This the base command name required to execute it. For example, in `?one two three` the parent name would be `one two`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

get_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.get_command "Permalink to this definition")

Get a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to get aliases.

The name could be fully qualified (e.g. `'foo bar'`) will get the subcommand `bar` of the group command `foo`. If a subcommand is not found then `None` is returned just as usual.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to get.

Returns

The command that was requested. If not found, returns `None`.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

get_cooldown_retry_after(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.get_cooldown_retry_after "Permalink to this definition")

Retrieves the amount of seconds before this command can be tried again.

New in version 1.4.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to retrieve the cooldown from.

Returns

The amount of time left on this command’s cooldown in seconds. If this is `0.0` then the command isn’t on cooldown.

Return type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

has_error_handler()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.has_error_handler "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks whether the command has an error handler registered.

New in version 1.7.

is_on_cooldown(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.is_on_cooldown "Permalink to this definition")

Checks whether the command is currently on cooldown.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to use when checking the commands cooldown status.

Returns

A boolean indicating if the command is on cooldown.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ parents[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.parents "Permalink to this definition")

Retrieves the parents of this command.

If the command has no parents then it returns an empty [`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)").

For example in commands `?a b c test`, the parents are `[c, b, a]`.

New in version 1.1.

Type

List[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.qualified_name "Permalink to this definition")

Retrieves the fully qualified command name.

This is the full parent name with the command name as well. For example, in `?one two three` the qualified name would be `one two three`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

remove_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.remove_check "Permalink to this definition")

Removes a check from the command.

This function is idempotent and will not raise an exception if the function is not in the command’s checks.

New in version 1.3.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function to remove from the checks.

remove_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.remove_command "Permalink to this definition")

Remove a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to remove aliases.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to remove.

Returns

The command that was removed. If the name is not valid then `None` is returned instead.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

reset_cooldown(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.reset_cooldown "Permalink to this definition")

Resets the cooldown on this command.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to reset the cooldown under.

_property_ root_parent[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.root_parent "Permalink to this definition")

Retrieves the root parent of this command.

If the command has no parents then it returns `None`.

For example in commands `?a b c test`, the root parent is `a`.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ short_doc[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.short_doc "Permalink to this definition")

Gets the “short” documentation of a command.

By default, this is the [`brief`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.brief "discord.ext.commands.Command.brief") attribute. If that lookup leads to an empty string then the first line of the [`help`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.help "discord.ext.commands.Command.help") attribute is used instead.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ signature[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.signature "Permalink to this definition")

Returns a POSIX-like signature useful for help command output.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

update(_**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.update "Permalink to this definition")

Updates [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") instance with updated attribute.

This works similarly to the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") decorator in terms of parameters in that they are passed to the [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") or subclass constructors, sans the name and callback.

_for ... in_ walk_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.walk_commands "Permalink to this definition")

An iterator that recursively walks through all commands and subcommands.

Changed in version 1.4: Duplicates due to aliases are no longer returned

Yields

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")] – A command or group from the internal list of commands.

### GroupMixin[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#groupmixin "Permalink to this headline")

_class_ discord.ext.commands.GroupMixin(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin "Permalink to this definition")

A mixin that implements common functionality for classes that behave similar to [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group") and are allowed to register commands.

all_commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.all_commands "Permalink to this definition")

A mapping of command name to [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") objects.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

case_insensitive[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.case_insensitive "Permalink to this definition")

Whether the commands should be case insensitive. Defaults to `False`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

@command(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.command "Permalink to this definition")

A shortcut decorator that invokes [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Command, adds it to the bot, then returns it.

Return type

Callable[…, [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

@group(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.group "Permalink to this definition")

A shortcut decorator that invokes [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.group "discord.ext.commands.group") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Group, adds it to the bot, then returns it.

Return type

Callable[…, [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.commands "Permalink to this definition")

A unique set of commands without aliases that are registered.

Type

Set[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

add_command(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "Permalink to this definition")

Adds a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") into the internal list of commands.

This is usually not called, instead the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.command "discord.ext.commands.GroupMixin.command") or [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.group "discord.ext.commands.GroupMixin.group") shortcut decorators are used instead.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to add.

Raises

*   [**CommandRegistrationError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError "discord.ext.commands.CommandRegistrationError") – If the command or its alias is already registered by different command.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the command passed is not a subclass of [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command").
    

remove_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.remove_command "Permalink to this definition")

Remove a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to remove aliases.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to remove.

Returns

The command that was removed. If the name is not valid then `None` is returned instead.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

_for ... in_ walk_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.walk_commands "Permalink to this definition")

An iterator that recursively walks through all commands and subcommands.

Changed in version 1.4: Duplicates due to aliases are no longer returned

Yields

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")] – A command or group from the internal list of commands.

get_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.get_command "Permalink to this definition")

Get a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to get aliases.

The name could be fully qualified (e.g. `'foo bar'`) will get the subcommand `bar` of the group command `foo`. If a subcommand is not found then `None` is returned just as usual.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to get.

Returns

The command that was requested. If not found, returns `None`.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

### HybridCommand[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#hybridcommand "Permalink to this headline")

_class_ discord.ext.commands.HybridCommand(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "Permalink to this definition")

A class that is both an application command and a regular text command.

This has the same parameters and attributes as a regular [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"). However, it also doubles as an [`application command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"). In order for this to work, the callbacks must have the same subset that is supported by application commands.

These are not created manually, instead they are created via the decorator or functional interface.

New in version 2.0.

@after_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand.after_invoke "Permalink to this definition")

A decorator that registers a coroutine as a post-invoke hook.

A post-invoke hook is called directly after the command is called. This makes it a useful function to clean-up database connections or any type of clean up required.

This post-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.after_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.after_invoke "discord.ext.commands.Bot.after_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the post-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@autocomplete(_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand.autocomplete "Permalink to this definition")

A decorator that registers a coroutine as an autocomplete prompt for a parameter.

This is the same as [`autocomplete()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.autocomplete "discord.app_commands.Command.autocomplete"). It is only applicable for the application command and doesn’t do anything if the command is a regular command.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The parameter name to register as autocomplete.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine or the parameter is not found or of an invalid type.

@before_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand.before_invoke "Permalink to this definition")

A decorator that registers a coroutine as a pre-invoke hook.

A pre-invoke hook is called directly before the command is called. This makes it a useful function to set up database connections or any type of set up required.

This pre-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "discord.ext.commands.Bot.before_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the pre-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@error[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

A local error handler is an [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event limited to a single command. However, the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") is still invoked afterwards as the catch-all.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

_await_ can_run(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand.can_run "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Checks if the command can be executed by checking all the predicates inside the [`checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") attribute. This also checks whether the command is disabled.

Changed in version 1.3: Checks whether the command is disabled or not

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The ctx of the command currently being invoked.

Raises

[**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – Any command error that was raised during a check call will be propagated by this function.

Returns

A boolean indicating if the command can be invoked.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

### HybridGroup[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#hybridgroup "Permalink to this headline")

_class_ discord.ext.commands.HybridGroup(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup "Permalink to this definition")

A class that is both an application command group and a regular text group.

This has the same parameters and attributes as a regular [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group"). However, it also doubles as an [`application command group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group"). Note that application commands groups cannot have callbacks associated with them, so the callback is only called if it’s not invoked as an application command.

Hybrid groups will always have [`Group.invoke_without_command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.invoke_without_command "discord.ext.commands.Group.invoke_without_command") set to `True`.

These are not created manually, instead they are created via the decorator or functional interface.

New in version 2.0.

fallback[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.fallback "Permalink to this definition")

The command name to use as a fallback for the application command. Since application command groups cannot be invoked, this creates a subcommand within the group that can be invoked with the given group callback. If `None` then no fallback command is given. Defaults to `None`.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

fallback_locale[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.fallback_locale "Permalink to this definition")

The fallback command name’s locale string, if available.

Type

Optional[[`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]

@after_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.after_invoke "Permalink to this definition")

A decorator that registers a coroutine as a post-invoke hook.

A post-invoke hook is called directly after the command is called. This makes it a useful function to clean-up database connections or any type of clean up required.

This post-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.after_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.after_invoke "discord.ext.commands.Bot.after_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the post-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@autocomplete(_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.autocomplete "Permalink to this definition")

A decorator that registers a coroutine as an autocomplete prompt for a parameter.

This is the same as [`autocomplete()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command.autocomplete "discord.app_commands.Command.autocomplete"). It is only applicable for the application command and doesn’t do anything if the command is a regular command.

This is only available if the group has a fallback application command registered.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The parameter name to register as autocomplete.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine or the parameter is not found or of an invalid type.

@before_invoke[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.before_invoke "Permalink to this definition")

A decorator that registers a coroutine as a pre-invoke hook.

A pre-invoke hook is called directly before the command is called. This makes it a useful function to set up database connections or any type of set up required.

This pre-invoke hook takes a sole parameter, a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

See [`Bot.before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.before_invoke "discord.ext.commands.Bot.before_invoke") for more info.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the pre-invoke hook.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@command(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.command "Permalink to this definition")

A shortcut decorator that invokes [`hybrid_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.hybrid_command "discord.ext.commands.hybrid_command") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.add_command "discord.ext.commands.HybridGroup.add_command").

Returns

A decorator that converts the provided method into a Command, adds it to the bot, then returns it.

Return type

Callable[…, [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand")]

@error[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.error "Permalink to this definition")

A decorator that registers a coroutine as a local error handler.

A local error handler is an [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event limited to a single command. However, the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") is still invoked afterwards as the catch-all.

Changed in version 2.0: `coro` parameter is now positional-only.

Parameters

**coro** ([coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")) – The coroutine to register as the local error handler.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The coroutine passed is not actually a coroutine.

@group(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.group "Permalink to this definition")

A shortcut decorator that invokes [`hybrid_group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.hybrid_group "discord.ext.commands.hybrid_group") and adds it to the internal command list via [`add_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.add_command "discord.ext.commands.GroupMixin.add_command").

Returns

A decorator that converts the provided method into a Group, adds it to the bot, then returns it.

Return type

Callable[…, [`HybridGroup`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup "discord.ext.commands.HybridGroup")]

_await_ can_run(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.can_run "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Checks if the command can be executed by checking all the predicates inside the [`checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") attribute. This also checks whether the command is disabled.

Changed in version 1.3: Checks whether the command is disabled or not

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The ctx of the command currently being invoked.

Raises

[**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – Any command error that was raised during a check call will be propagated by this function.

Returns

A boolean indicating if the command can be invoked.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

add_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.add_check "Permalink to this definition")

Adds a check to the command.

This is the non-decorator interface to [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check").

New in version 1.3.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function that will be used as a check.

add_command(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.add_command "Permalink to this definition")

Adds a [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand") into the internal list of commands.

This is usually not called, instead the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.command "discord.ext.commands.GroupMixin.command") or [`group()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupMixin.group "discord.ext.commands.GroupMixin.group") shortcut decorators are used instead.

Parameters

**command** ([`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand")) – The command to add.

Raises

*   [**CommandRegistrationError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError "discord.ext.commands.CommandRegistrationError") – If the command or its alias is already registered by different command.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – If the command passed is not a subclass of [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand").
    

_property_ clean_params[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.clean_params "Permalink to this definition")

Dict[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")]: Retrieves the parameter dictionary without the context or self parameters.

Useful for inspecting signature.

_property_ cog_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.cog_name "Permalink to this definition")

The name of the cog this command belongs to, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.commands "Permalink to this definition")

A unique set of commands without aliases that are registered.

Type

Set[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

_property_ cooldown[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.cooldown "Permalink to this definition")

The cooldown of a command when invoked or `None` if the command doesn’t have a registered cooldown.

New in version 2.0.

Type

Optional[[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")]

copy()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.copy "Permalink to this definition")

Creates a copy of this [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group").

Returns

A new instance of this group.

Return type

[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")

_property_ full_parent_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.full_parent_name "Permalink to this definition")

Retrieves the fully qualified parent command name.

This the base command name required to execute it. For example, in `?one two three` the parent name would be `one two`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

get_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.get_command "Permalink to this definition")

Get a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to get aliases.

The name could be fully qualified (e.g. `'foo bar'`) will get the subcommand `bar` of the group command `foo`. If a subcommand is not found then `None` is returned just as usual.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to get.

Returns

The command that was requested. If not found, returns `None`.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

get_cooldown_retry_after(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.get_cooldown_retry_after "Permalink to this definition")

Retrieves the amount of seconds before this command can be tried again.

New in version 1.4.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to retrieve the cooldown from.

Returns

The amount of time left on this command’s cooldown in seconds. If this is `0.0` then the command isn’t on cooldown.

Return type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

has_error_handler()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.has_error_handler "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks whether the command has an error handler registered.

New in version 1.7.

is_on_cooldown(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.is_on_cooldown "Permalink to this definition")

Checks whether the command is currently on cooldown.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to use when checking the commands cooldown status.

Returns

A boolean indicating if the command is on cooldown.

Return type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ parents[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.parents "Permalink to this definition")

Retrieves the parents of this command.

If the command has no parents then it returns an empty [`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)").

For example in commands `?a b c test`, the parents are `[c, b, a]`.

New in version 1.1.

Type

List[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.qualified_name "Permalink to this definition")

Retrieves the fully qualified command name.

This is the full parent name with the command name as well. For example, in `?one two three` the qualified name would be `one two three`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

remove_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.remove_check "Permalink to this definition")

Removes a check from the command.

This function is idempotent and will not raise an exception if the function is not in the command’s checks.

New in version 1.3.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function to remove from the checks.

reset_cooldown(_ctx_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.reset_cooldown "Permalink to this definition")

Resets the cooldown on this command.

Changed in version 2.0: `ctx` parameter is now positional-only.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to reset the cooldown under.

_property_ root_parent[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.root_parent "Permalink to this definition")

Retrieves the root parent of this command.

If the command has no parents then it returns `None`.

For example in commands `?a b c test`, the root parent is `a`.

Type

Optional[[`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")]

_property_ short_doc[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.short_doc "Permalink to this definition")

Gets the “short” documentation of a command.

By default, this is the [`brief`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.brief "discord.ext.commands.Command.brief") attribute. If that lookup leads to an empty string then the first line of the [`help`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.help "discord.ext.commands.Command.help") attribute is used instead.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ signature[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.signature "Permalink to this definition")

Returns a POSIX-like signature useful for help command output.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

update(_**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.update "Permalink to this definition")

Updates [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") instance with updated attribute.

This works similarly to the [`command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.command "discord.ext.commands.command") decorator in terms of parameters in that they are passed to the [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") or subclass constructors, sans the name and callback.

_for ... in_ walk_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.walk_commands "Permalink to this definition")

An iterator that recursively walks through all commands and subcommands.

Changed in version 1.4: Duplicates due to aliases are no longer returned

Yields

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")] – A command or group from the internal list of commands.

remove_command(_name_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridGroup.remove_command "Permalink to this definition")

Remove a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") from the internal list of commands.

This could also be used as a way to remove aliases.

Changed in version 2.0: `name` parameter is now positional-only.

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the command to remove.

Returns

The command that was removed. If the name is not valid then `None` is returned instead.

Return type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

## Cogs[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#cogs "Permalink to this headline")

### Cog[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#cog "Permalink to this headline")

_class_ discord.ext.commands.Cog(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "Permalink to this definition")

The base class that all cogs must inherit from.

A cog is a collection of commands, listeners, and optional state to help group commands together. More information on them can be found on the [Cogs](https://discordpy.readthedocs.io/en/stable/ext/commands/cogs.html#ext-commands-cogs) page.

When inheriting from this class, the options shown in [`CogMeta`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta "discord.ext.commands.CogMeta") are equally valid here.

get_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.get_commands "Permalink to this definition")

Returns the commands that are defined inside this cog.

This does _not_ include [`discord.app_commands.Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command") or [`discord.app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group") instances.

Returns

A [`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)") of [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")s that are defined inside this cog, not including subcommands.

Return type

List[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

get_app_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.get_app_commands "Permalink to this definition")

Returns the app commands that are defined inside this cog.

Returns

A [`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)") of [`discord.app_commands.Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command")s and [`discord.app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")s that are defined inside this cog, not including subcommands.

Return type

List[Union[[`discord.app_commands.Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`discord.app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]]

_property_ qualified_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.qualified_name "Permalink to this definition")

Returns the cog’s specified name, not the class name.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.description "Permalink to this definition")

Returns the cog’s description, typically the cleaned docstring.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_for ... in_ walk_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.walk_commands "Permalink to this definition")

An iterator that recursively walks through this cog’s commands and subcommands.

Yields

Union[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"), [`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")] – A command or group from the cog.

_for ... in_ walk_app_commands()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.walk_app_commands "Permalink to this definition")

An iterator that recursively walks through this cog’s app commands and subcommands.

Yields

Union[[`discord.app_commands.Command`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Command "discord.app_commands.Command"), [`discord.app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")] – An app command or group from the cog.

_property_ app_command[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.app_command "Permalink to this definition")

Returns the associated group with this cog.

This is only available if inheriting from [`GroupCog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog "discord.ext.commands.GroupCog").

Type

Optional[[`discord.app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group")]

get_listeners()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.get_listeners "Permalink to this definition")

Returns a [`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)") of (name, function) listener pairs that are defined in this cog.

Returns

The listeners defined in this cog.

Return type

List[Tuple[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)")]]

_classmethod_ listener(_name=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.listener "Permalink to this definition")

A decorator that marks a function as a listener.

This is the cog equivalent of [`Bot.listen()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.listen "discord.ext.commands.Bot.listen").

Parameters

**name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The name of the event being listened to. If not provided, it defaults to the function’s name.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The function is not a coroutine function or a string was not passed as the name.

has_error_handler()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.has_error_handler "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks whether the cog has an error handler.

New in version 1.7.

has_app_command_error_handler()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.has_app_command_error_handler "Permalink to this definition")

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)"): Checks whether the cog has an app error handler.

New in version 2.1.

_await_ cog_load()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_load "Permalink to this definition")

This function _could be a_ [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A special method that is called when the cog gets loaded.

Subclasses must replace this if they want special asynchronous loading behaviour. Note that the `__init__` special method does not allow asynchronous code to run inside it, thus this is helpful for setting up code that needs to be asynchronous.

New in version 2.0.

_await_ cog_unload()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_unload "Permalink to this definition")

This function _could be a_ [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A special method that is called when the cog gets removed.

Subclasses must replace this if they want special unloading behaviour.

Exceptions raised in this method are ignored during extension unloading.

Changed in version 2.0: This method can now be a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine "(in Python v3.13)").

bot_check_once(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.bot_check_once "Permalink to this definition")

A special method that registers as a [`Bot.check_once()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check_once "discord.ext.commands.Bot.check_once") check.

This function **can** be a coroutine and must take a sole parameter, `ctx`, to represent the [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

bot_check(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.bot_check "Permalink to this definition")

A special method that registers as a [`Bot.check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.check "discord.ext.commands.Bot.check") check.

This function **can** be a coroutine and must take a sole parameter, `ctx`, to represent the [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

cog_check(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_check "Permalink to this definition")

A special method that registers as a [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") for every command and subcommand in this cog.

This function **can** be a coroutine and must take a sole parameter, `ctx`, to represent the [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context").

interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.interaction_check "Permalink to this definition")

A special method that registers as a [`discord.app_commands.check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") for every app command and subcommand in this cog.

This function **can** be a coroutine and must take a sole parameter, `interaction`, to represent the [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction").

New in version 2.0.

_await_ cog_command_error(_ctx_, _error_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_command_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A special method that is called whenever an error is dispatched inside this cog.

This is similar to [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") except only applying to the commands inside this cog.

This **must** be a coroutine.

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context where the error happened.
    
*   **error** ([`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")) – The error that happened.
    

_await_ cog_app_command_error(_interaction_, _error_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_app_command_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A special method that is called whenever an error within an application command is dispatched inside this cog.

This is similar to [`discord.app_commands.CommandTree.on_error()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.CommandTree.on_error "discord.app_commands.CommandTree.on_error") except only applying to the application commands inside this cog.

This **must** be a coroutine.

Parameters

*   **interaction** ([`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction that is being handled.
    
*   **error** ([`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError")) – The exception that was raised.
    

_await_ cog_before_invoke(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_before_invoke "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A special method that acts as a cog local pre-invoke hook.

This is similar to [`Command.before_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.before_invoke "discord.ext.commands.Command.before_invoke").

This **must** be a coroutine.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.

_await_ cog_after_invoke(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog.cog_after_invoke "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A special method that acts as a cog local post-invoke hook.

This is similar to [`Command.after_invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.after_invoke "discord.ext.commands.Command.after_invoke").

This **must** be a coroutine.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.

### GroupCog[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#groupcog "Permalink to this headline")

_class_ discord.ext.commands.GroupCog(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog "Permalink to this definition")

Represents a cog that also doubles as a parent [`discord.app_commands.Group`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Group "discord.app_commands.Group") for the application commands defined within it.

This inherits from [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog") and the options in [`CogMeta`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta "discord.ext.commands.CogMeta") also apply to this. See the [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog") documentation for methods.

Decorators such as [`guild_only()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guild_only "discord.app_commands.guild_only"), [`guilds()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guilds "discord.app_commands.guilds"), and [`default_permissions()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.default_permissions "discord.app_commands.default_permissions") will apply to the group if used on top of the cog.

Hybrid commands will also be added to the Group, giving the ability to categorize slash commands into groups, while keeping the prefix-style command as a root-level command.

For example:

content_copy

```
from discord import app_commands
from discord.ext import commands

@app_commands.guild_only()
class MyCog(commands.GroupCog, group_name='my-cog'):
    pass
```

New in version 2.0.

interaction_check(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog.interaction_check "Permalink to this definition")

A special method that registers as a [`discord.app_commands.check()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.check "discord.app_commands.check") for every app command and subcommand in this cog.

This function **can** be a coroutine and must take a sole parameter, `interaction`, to represent the [`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction").

New in version 2.0.

### CogMeta[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#cogmeta "Permalink to this headline")

_class_ discord.ext.commands.CogMeta(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta "Permalink to this definition")

A metaclass for defining a cog.

Note that you should probably not use this directly. It is exposed purely for documentation purposes along with making custom metaclasses to intermix with other metaclasses such as the [`abc.ABCMeta`](https://docs.python.org/3/library/abc.html#abc.ABCMeta "(in Python v3.13)") metaclass.

For example, to create an abstract cog mixin class, the following would be done.

content_copy

```
import abc

class CogABCMeta(commands.CogMeta, abc.ABCMeta):
    pass

class SomeMixin(metaclass=abc.ABCMeta):
    pass

class SomeCogMixin(SomeMixin, commands.Cog, metaclass=CogABCMeta):
    pass
```

Note

When passing an attribute of a metaclass that is documented below, note that you must pass it as a keyword-only argument to the class creation like the following example:

content_copy

```
class MyCog(commands.Cog, name='My Cog'):
    pass
```

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.name "Permalink to this definition")

The cog name. By default, it is the name of the class with no modification.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.description "Permalink to this definition")

The cog description. By default, it is the cleaned docstring of the class.

New in version 1.6.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

command_attrs[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.command_attrs "Permalink to this definition")

A list of attributes to apply to every command inside this cog. The dictionary is passed into the [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") options at `__init__`. If you specify attributes inside the command attribute in the class, it will override the one specified inside this attribute. For example:

content_copy

```
class MyCog(commands.Cog, command_attrs=dict(hidden=True)):
 @commands.command()
    async def foo(self, ctx):
        pass # hidden -> True

 @commands.command(hidden=False)
    async def bar(self, ctx):
        pass # hidden -> False
```

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

group_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.group_name "Permalink to this definition")

The group name of a cog. This is only applicable for [`GroupCog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog "discord.ext.commands.GroupCog") instances. By default, it’s the same value as [`name`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.name "discord.ext.commands.CogMeta.name").

New in version 2.0.

Type

Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]

group_description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.group_description "Permalink to this definition")

The group description of a cog. This is only applicable for [`GroupCog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog "discord.ext.commands.GroupCog") instances. By default, it’s the same value as [`description`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.description "discord.ext.commands.CogMeta.description").

New in version 2.0.

Type

Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str")]

group_nsfw[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.group_nsfw "Permalink to this definition")

Whether the application command group is NSFW. This is only applicable for [`GroupCog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog "discord.ext.commands.GroupCog") instances. By default, it’s `False`.

New in version 2.0.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

group_auto_locale_strings[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.group_auto_locale_strings "Permalink to this definition")

If this is set to `True`, then all translatable strings will implicitly be wrapped into [`locale_str`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.locale_str "discord.app_commands.locale_str") rather than [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"). Defaults to `True`.

New in version 2.0.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

group_extras[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CogMeta.group_extras "Permalink to this definition")

A dictionary that can be used to store extraneous data. This is only applicable for [`GroupCog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GroupCog "discord.ext.commands.GroupCog") instances. The library will not touch any values or keys within this dictionary.

New in version 2.1.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

## Help Commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#help-commands "Permalink to this headline")

### HelpCommand[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#helpcommand "Permalink to this headline")

_class_ discord.ext.commands.HelpCommand(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand "Permalink to this definition")

The base implementation for help command formatting.

Note

Internally instances of this class are deep copied every time the command itself is invoked to prevent a race condition mentioned in [GH-2123](https://github.com/Rapptz/discord.py/issues/2123).

This means that relying on the state of this class to be the same between command invocations would not work as expected.

context[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.context "Permalink to this definition")

The context that invoked this help formatter. This is generally set after the help command assigned, [`command_callback()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_callback "discord.ext.commands.HelpCommand.command_callback"), has been called.

Type

Optional[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")]

show_hidden[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.show_hidden "Permalink to this definition")

Specifies if hidden commands should be shown in the output. Defaults to `False`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

verify_checks[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.verify_checks "Permalink to this definition")

Specifies if commands should have their [`Command.checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") called and verified. If `True`, always calls [`Command.checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks"). If `None`, only calls [`Command.checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") in a guild setting. If `False`, never calls [`Command.checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks"). Defaults to `True`.

Changed in version 1.7.

Type

Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]

command_attrs[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_attrs "Permalink to this definition")

A dictionary of options to pass in for the construction of the help command. This allows you to change the command behaviour without actually changing the implementation of the command. The attributes will be the same as the ones passed in the [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") constructor.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

add_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.add_check "Permalink to this definition")

Adds a check to the help command.

New in version 1.4.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function that will be used as a check.

remove_check(_func_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.remove_check "Permalink to this definition")

Removes a check from the help command.

This function is idempotent and will not raise an exception if the function is not in the command’s checks.

New in version 1.4.

Changed in version 2.0: `func` parameter is now positional-only.

Parameters

**func** – The function to remove from the checks.

get_bot_mapping()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_bot_mapping "Permalink to this definition")

Retrieves the bot mapping passed to [`send_bot_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_bot_help "discord.ext.commands.HelpCommand.send_bot_help").

_property_ invoked_with[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.invoked_with "Permalink to this definition")

Similar to [`Context.invoked_with`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoked_with "discord.ext.commands.Context.invoked_with") except properly handles the case where [`Context.send_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.send_help "discord.ext.commands.Context.send_help") is used.

If the help command was used regularly then this returns the [`Context.invoked_with`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoked_with "discord.ext.commands.Context.invoked_with") attribute. Otherwise, if it the help command was called using [`Context.send_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.send_help "discord.ext.commands.Context.send_help") then it returns the internal command name of the help command.

Returns

The command name that triggered this invocation.

Return type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

get_command_signature(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_command_signature "Permalink to this definition")

Retrieves the signature portion of the help page.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to get the signature of.

Returns

The signature for the command.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

remove_mentions(_string_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.remove_mentions "Permalink to this definition")

Removes mentions from the string to prevent abuse.

This includes `@everyone`, `@here`, member mentions and role mentions.

Changed in version 2.0: `string` parameter is now positional-only.

Returns

The string with mentions removed.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ cog[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.cog "Permalink to this definition")

A property for retrieving or setting the cog for the help command.

When a cog is set for the help command, it is as-if the help command belongs to that cog. All cog special methods will apply to the help command and it will be automatically unset on unload.

To unbind the cog from the help command, you can set it to `None`.

Returns

The cog that is currently set for the help command.

Return type

Optional[[`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")]

command_not_found(_string_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_not_found "Permalink to this definition")

This function _could be a_ [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A method called when a command is not found in the help command. This is useful to override for i18n.

Defaults to `No command called {0} found.`

Changed in version 2.0: `string` parameter is now positional-only.

Parameters

**string** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The string that contains the invalid command. Note that this has had mentions removed to prevent abuse.

Returns

The string to use when a command has not been found.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

subcommand_not_found(_command_, _string_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.subcommand_not_found "Permalink to this definition")

This function _could be a_ [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A method called when a command did not have a subcommand requested in the help command. This is useful to override for i18n.

Defaults to either:

*   `'Command "{command.qualified_name}" has no subcommands.'`
    
    *   If there is no subcommand in the `command` parameter.
        
    
*   `'Command "{command.qualified_name}" has no subcommand named {string}'`
    
    *   If the `command` parameter has subcommands but not one named `string`.
        
    

Changed in version 2.0: `command` and `string` parameters are now positional-only.

Parameters

*   **command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command that did not have the subcommand requested.
    
*   **string** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The string that contains the invalid subcommand. Note that this has had mentions removed to prevent abuse.
    

Returns

The string to use when the command did not have the subcommand requested.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_await_ filter_commands(_commands_, _/_, _*_, _sort=False_, _key=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.filter_commands "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Returns a filtered list of commands and optionally sorts them.

This takes into account the [`verify_checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.verify_checks "discord.ext.commands.HelpCommand.verify_checks") and [`show_hidden`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.show_hidden "discord.ext.commands.HelpCommand.show_hidden") attributes.

Changed in version 2.0: `commands` parameter is now positional-only.

Parameters

*   **commands** (Iterable[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]) – An iterable of commands that are getting filtered.
    
*   **sort** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to sort the result.
    
*   **key** (Optional[Callable[[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")], Any]]) – An optional key function to pass to [`sorted()`](https://docs.python.org/3/library/functions.html#sorted "(in Python v3.13)") that takes a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") as its sole parameter. If `sort` is passed as `True` then this will default as the command name.
    

Returns

A list of commands that passed the filter.

Return type

List[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

get_max_size(_commands_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_max_size "Permalink to this definition")

Returns the largest name length of the specified command list.

Changed in version 2.0: `commands` parameter is now positional-only.

Parameters

**commands** (Sequence[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]) – A sequence of commands to check for the largest size.

Returns

The maximum width of the commands.

Return type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

get_destination()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "Permalink to this definition")

Returns the [`Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable") where the help command will be output.

You can override this method to customise the behaviour.

By default this returns the context’s channel.

Returns

The destination where the help command will be output.

Return type

[`abc.Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable")

_await_ send_error_message(_error_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_error_message "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Handles the implementation when an error happens in the help command. For example, the result of [`command_not_found()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_not_found "discord.ext.commands.HelpCommand.command_not_found") will be passed here.

You can override this method to customise the behaviour.

By default, this sends the error message to the destination specified by [`get_destination()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "discord.ext.commands.HelpCommand.get_destination").

Changed in version 2.0: `error` parameter is now positional-only.

Parameters

**error** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The error message to display to the user. Note that this has had mentions removed to prevent abuse.

_await_ on_help_command_error(_ctx_, _error_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.on_help_command_error "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The help command’s error handler, as specified by [Error Handling](https://discordpy.readthedocs.io/en/stable/ext/commands/commands.html#ext-commands-error-handler).

Useful to override if you need some specific behaviour when the error handler is called.

By default this method does nothing and just propagates to the default error handlers.

Changed in version 2.0: `ctx` and `error` parameters are now positional-only.

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.
    
*   **error** ([`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")) – The error that was raised.
    

_await_ send_bot_help(_mapping_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_bot_help "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Handles the implementation of the bot command page in the help command. This function is called when the help command is called with no arguments.

It should be noted that this method does not return anything – rather the actual message sending should be done inside this method. Well behaved subclasses should use [`get_destination()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "discord.ext.commands.HelpCommand.get_destination") to know where to send, as this is a customisation point for other users.

You can override this method to customise the behaviour.

Note

You can access the invocation context with [`HelpCommand.context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.context "discord.ext.commands.HelpCommand.context").

Also, the commands in the mapping are not filtered. To do the filtering you will have to call [`filter_commands()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.filter_commands "discord.ext.commands.HelpCommand.filter_commands") yourself.

Changed in version 2.0: `mapping` parameter is now positional-only.

Parameters

**mapping** (Mapping[Optional[[`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")], List[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]]) – A mapping of cogs to commands that have been requested by the user for help. The key of the mapping is the [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog") that the command belongs to, or `None` if there isn’t one, and the value is a list of commands that belongs to that cog.

_await_ send_cog_help(_cog_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_cog_help "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Handles the implementation of the cog page in the help command. This function is called when the help command is called with a cog as the argument.

It should be noted that this method does not return anything – rather the actual message sending should be done inside this method. Well behaved subclasses should use [`get_destination()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "discord.ext.commands.HelpCommand.get_destination") to know where to send, as this is a customisation point for other users.

You can override this method to customise the behaviour.

Changed in version 2.0: `cog` parameter is now positional-only.

Parameters

**cog** ([`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")) – The cog that was requested for help.

_await_ send_group_help(_group_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_group_help "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Handles the implementation of the group page in the help command. This function is called when the help command is called with a group as the argument.

It should be noted that this method does not return anything – rather the actual message sending should be done inside this method. Well behaved subclasses should use [`get_destination()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "discord.ext.commands.HelpCommand.get_destination") to know where to send, as this is a customisation point for other users.

You can override this method to customise the behaviour.

Note

You can access the invocation context with [`HelpCommand.context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.context "discord.ext.commands.HelpCommand.context").

To get the commands that belong to this group without aliases see [`Group.commands`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group.commands "discord.ext.commands.Group.commands"). The commands returned not filtered. To do the filtering you will have to call [`filter_commands()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.filter_commands "discord.ext.commands.HelpCommand.filter_commands") yourself.

Changed in version 2.0: `group` parameter is now positional-only.

Parameters

**group** ([`Group`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Group "discord.ext.commands.Group")) – The group that was requested for help.

_await_ send_command_help(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_command_help "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Handles the implementation of the single command page in the help command.

It should be noted that this method does not return anything – rather the actual message sending should be done inside this method. Well behaved subclasses should use [`get_destination()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "discord.ext.commands.HelpCommand.get_destination") to know where to send, as this is a customisation point for other users.

You can override this method to customise the behaviour.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command that was requested for help.

_await_ prepare_help_command(_ctx_, _command=None_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.prepare_help_command "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A low level method that can be used to prepare the help command before it does anything. For example, if you need to prepare some state in your subclass before the command does its processing then this would be the place to do it.

The default implementation does nothing.

Note

This is called _inside_ the help command callback body. So all the usual rules that happen inside apply here as well.

Changed in version 2.0: `ctx` and `command` parameters are now positional-only.

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.
    
*   **command** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The argument passed to the help command.
    

_await_ command_callback(_ctx_, _/_, _*_, _command=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_callback "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The actual implementation of the help command.

It is not recommended to override this method and instead change the behaviour through the methods that actually get dispatched.

*   [`send_bot_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_bot_help "discord.ext.commands.HelpCommand.send_bot_help")
    
*   [`send_cog_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_cog_help "discord.ext.commands.HelpCommand.send_cog_help")
    
*   [`send_group_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_group_help "discord.ext.commands.HelpCommand.send_group_help")
    
*   [`send_command_help()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_command_help "discord.ext.commands.HelpCommand.send_command_help")
    
*   [`get_destination()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_destination "discord.ext.commands.HelpCommand.get_destination")
    
*   [`command_not_found()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_not_found "discord.ext.commands.HelpCommand.command_not_found")
    
*   [`subcommand_not_found()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.subcommand_not_found "discord.ext.commands.HelpCommand.subcommand_not_found")
    
*   [`send_error_message()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.send_error_message "discord.ext.commands.HelpCommand.send_error_message")
    
*   [`on_help_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.on_help_command_error "discord.ext.commands.HelpCommand.on_help_command_error")
    
*   [`prepare_help_command()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.prepare_help_command "discord.ext.commands.HelpCommand.prepare_help_command")
    

Changed in version 2.0: `ctx` parameter is now positional-only.

### DefaultHelpCommand[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#defaulthelpcommand "Permalink to this headline")

_class_ discord.ext.commands.DefaultHelpCommand(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand "Permalink to this definition")

The implementation of the default help command.

This inherits from [`HelpCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand "discord.ext.commands.HelpCommand").

It extends it with the following attributes.

width[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.width "Permalink to this definition")

The maximum number of characters that fit in a line. Defaults to 80.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

sort_commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.sort_commands "Permalink to this definition")

Whether to sort the commands in the output alphabetically. Defaults to `True`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

dm_help[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.dm_help "Permalink to this definition")

A tribool that indicates if the help command should DM the user instead of sending it to the channel it received it from. If the boolean is set to `True`, then all help output is DM’d. If `False`, none of the help output is DM’d. If `None`, then the bot will only DM when the help message becomes too long (dictated by more than [`dm_help_threshold`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.dm_help_threshold "discord.ext.commands.DefaultHelpCommand.dm_help_threshold") characters). Defaults to `False`.

Type

Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]

dm_help_threshold[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.dm_help_threshold "Permalink to this definition")

The number of characters the paginator must accumulate before getting DM’d to the user if [`dm_help`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.dm_help "discord.ext.commands.DefaultHelpCommand.dm_help") is set to `None`. Defaults to 1000.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

indent[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.indent "Permalink to this definition")

How much to indent the commands from a heading. Defaults to `2`.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

arguments_heading[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.arguments_heading "Permalink to this definition")

The arguments list’s heading string used when the help command is invoked with a command name. Useful for i18n. Defaults to `"Arguments:"`. Shown when [`show_parameter_descriptions`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.show_parameter_descriptions "discord.ext.commands.DefaultHelpCommand.show_parameter_descriptions") is `True`.

New in version 2.0.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

show_parameter_descriptions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.show_parameter_descriptions "Permalink to this definition")

Whether to show the parameter descriptions. Defaults to `True`. Setting this to `False` will revert to showing the [`signature`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.signature "discord.ext.commands.Command.signature") instead.

New in version 2.0.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

commands_heading[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.commands_heading "Permalink to this definition")

The command list’s heading string used when the help command is invoked with a category name. Useful for i18n. Defaults to `"Commands:"`

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

default_argument_description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.default_argument_description "Permalink to this definition")

The default argument description string used when the argument’s [`description`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.description "discord.ext.commands.Parameter.description") is `None`. Useful for i18n. Defaults to `"No description given."`

New in version 2.0.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

no_category[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.no_category "Permalink to this definition")

The string used when there is a command which does not belong to any category(cog). Useful for i18n. Defaults to `"No Category"`

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

paginator[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.paginator "Permalink to this definition")

The paginator used to paginate the help command output.

Type

[`Paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator "discord.ext.commands.Paginator")

shorten_text(_text_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.shorten_text "Permalink to this definition")

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"): Shortens text to fit into the [`width`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.width "discord.ext.commands.DefaultHelpCommand.width").

Changed in version 2.0: `text` parameter is now positional-only.

get_ending_note()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.get_ending_note "Permalink to this definition")

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"): Returns help command’s ending note. This is mainly useful to override for i18n purposes.

get_command_signature(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.get_command_signature "Permalink to this definition")

Retrieves the signature portion of the help page.

Calls [`get_command_signature()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_command_signature "discord.ext.commands.HelpCommand.get_command_signature") if [`show_parameter_descriptions`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.show_parameter_descriptions "discord.ext.commands.DefaultHelpCommand.show_parameter_descriptions") is `False` else returns a modified signature where the command parameters are not shown.

New in version 2.0.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to get the signature of.

Returns

The signature for the command.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

add_indented_commands(_commands_, _/_, _*_, _heading_, _max_size=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.add_indented_commands "Permalink to this definition")

Indents a list of commands after the specified heading.

The formatting is added to the [`paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.paginator "discord.ext.commands.DefaultHelpCommand.paginator").

The default implementation is the command name indented by [`indent`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.indent "discord.ext.commands.DefaultHelpCommand.indent") spaces, padded to `max_size` followed by the command’s [`Command.short_doc`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.short_doc "discord.ext.commands.Command.short_doc") and then shortened to fit into the [`width`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.width "discord.ext.commands.DefaultHelpCommand.width").

Changed in version 2.0: `commands` parameter is now positional-only.

Parameters

*   **commands** (Sequence[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]) – A list of commands to indent for output.
    
*   **heading** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The heading to add to the output. This is only added if the list of commands is greater than 0.
    
*   **max_size** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The max size to use for the gap between indents. If unspecified, calls [`get_max_size()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_max_size "discord.ext.commands.HelpCommand.get_max_size") on the commands parameter.
    

add_command_arguments(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.add_command_arguments "Permalink to this definition")

Indents a list of command arguments after the [`arguments_heading`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.arguments_heading "discord.ext.commands.DefaultHelpCommand.arguments_heading").

The default implementation is the argument [`name`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.name "discord.ext.commands.Parameter.name") indented by [`indent`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.indent "discord.ext.commands.DefaultHelpCommand.indent") spaces, padded to `max_size` using [`get_max_size()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.get_max_size "discord.ext.commands.HelpCommand.get_max_size") followed by the argument’s [`description`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.description "discord.ext.commands.Parameter.description") or [`default_argument_description`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.default_argument_description "discord.ext.commands.DefaultHelpCommand.default_argument_description") and then shortened to fit into the [`width`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.width "discord.ext.commands.DefaultHelpCommand.width") and then [`displayed_default`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.displayed_default "discord.ext.commands.Parameter.displayed_default") between () if one is present after that.

New in version 2.0.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to list the arguments for.

_await_ send_pages()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.send_pages "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A helper utility to send the page output from [`paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.paginator "discord.ext.commands.DefaultHelpCommand.paginator") to the destination.

add_command_formatting(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.add_command_formatting "Permalink to this definition")

A utility function to format the non-indented block of commands and groups.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to format.

get_destination()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DefaultHelpCommand.get_destination "Permalink to this definition")

Returns the [`Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable") where the help command will be output.

You can override this method to customise the behaviour.

By default this returns the context’s channel.

Returns

The destination where the help command will be output.

Return type

[`abc.Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable")

### MinimalHelpCommand[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#minimalhelpcommand "Permalink to this headline")

_class_ discord.ext.commands.MinimalHelpCommand(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand "Permalink to this definition")

An implementation of a help command with minimal output.

This inherits from [`HelpCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand "discord.ext.commands.HelpCommand").

sort_commands[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.sort_commands "Permalink to this definition")

Whether to sort the commands in the output alphabetically. Defaults to `True`.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

commands_heading[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.commands_heading "Permalink to this definition")

The command list’s heading string used when the help command is invoked with a category name. Useful for i18n. Defaults to `"Commands"`

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

aliases_heading[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.aliases_heading "Permalink to this definition")

The alias list’s heading string used to list the aliases of the command. Useful for i18n. Defaults to `"Aliases:"`.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

dm_help[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.dm_help "Permalink to this definition")

A tribool that indicates if the help command should DM the user instead of sending it to the channel it received it from. If the boolean is set to `True`, then all help output is DM’d. If `False`, none of the help output is DM’d. If `None`, then the bot will only DM when the help message becomes too long (dictated by more than [`dm_help_threshold`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.dm_help_threshold "discord.ext.commands.MinimalHelpCommand.dm_help_threshold") characters). Defaults to `False`.

Type

Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]

dm_help_threshold[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.dm_help_threshold "Permalink to this definition")

The number of characters the paginator must accumulate before getting DM’d to the user if [`dm_help`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.dm_help "discord.ext.commands.MinimalHelpCommand.dm_help") is set to `None`. Defaults to 1000.

Type

Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

no_category[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.no_category "Permalink to this definition")

The string used when there is a command which does not belong to any category(cog). Useful for i18n. Defaults to `"No Category"`

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

paginator[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.paginator "Permalink to this definition")

The paginator used to paginate the help command output.

Type

[`Paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator "discord.ext.commands.Paginator")

_await_ send_pages()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.send_pages "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A helper utility to send the page output from [`paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.paginator "discord.ext.commands.MinimalHelpCommand.paginator") to the destination.

get_opening_note()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.get_opening_note "Permalink to this definition")

Returns help command’s opening note. This is mainly useful to override for i18n purposes.

The default implementation returns

content_copy

```
Use `{prefix}{command_name} [command]` for more info on a command.
You can also use `{prefix}{command_name} [category]` for more info on a category.
```

Returns

The help command opening note.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

get_command_signature(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.get_command_signature "Permalink to this definition")

Retrieves the signature portion of the help page.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to get the signature of.

Returns

The signature for the command.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

get_ending_note()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.get_ending_note "Permalink to this definition")

Return the help command’s ending note. This is mainly useful to override for i18n purposes.

The default implementation does nothing.

Returns

The help command ending note.

Return type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

add_bot_commands_formatting(_commands_, _heading_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.add_bot_commands_formatting "Permalink to this definition")

Adds the minified bot heading with commands to the output.

The formatting should be added to the [`paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.paginator "discord.ext.commands.MinimalHelpCommand.paginator").

The default implementation is a bold underline heading followed by commands separated by an EN SPACE (U+2002) in the next line.

Changed in version 2.0: `commands` and `heading` parameters are now positional-only.

Parameters

*   **commands** (Sequence[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]) – A list of commands that belong to the heading.
    
*   **heading** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The heading to add to the line.
    

add_subcommand_formatting(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.add_subcommand_formatting "Permalink to this definition")

Adds formatting information on a subcommand.

The formatting should be added to the [`paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.paginator "discord.ext.commands.MinimalHelpCommand.paginator").

The default implementation is the prefix and the [`Command.qualified_name`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.qualified_name "discord.ext.commands.Command.qualified_name") optionally followed by an En dash and the command’s [`Command.short_doc`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.short_doc "discord.ext.commands.Command.short_doc").

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to show information of.

add_aliases_formatting(_aliases_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.add_aliases_formatting "Permalink to this definition")

Adds the formatting information on a command’s aliases.

The formatting should be added to the [`paginator`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.paginator "discord.ext.commands.MinimalHelpCommand.paginator").

The default implementation is the [`aliases_heading`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.aliases_heading "discord.ext.commands.MinimalHelpCommand.aliases_heading") bolded followed by a comma separated list of aliases.

This is not called if there are no aliases to format.

Changed in version 2.0: `aliases` parameter is now positional-only.

Parameters

**aliases** (Sequence[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – A list of aliases to format.

add_command_formatting(_command_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.add_command_formatting "Permalink to this definition")

A utility function to format commands and groups.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

**command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command to format.

get_destination()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MinimalHelpCommand.get_destination "Permalink to this definition")

Returns the [`Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable") where the help command will be output.

You can override this method to customise the behaviour.

By default this returns the context’s channel.

Returns

The destination where the help command will be output.

Return type

[`abc.Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable")

### Paginator[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#paginator "Permalink to this headline")

_class_ discord.ext.commands.Paginator(_prefix='```'_, _suffix='```'_, _max_size=2000_, _linesep='\n'_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator "Permalink to this definition")

A class that aids in paginating code blocks for Discord messages.

len(x)

Returns the total number of characters in the paginator.

prefix[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.prefix "Permalink to this definition")

The prefix inserted to every page. e.g. three backticks, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

suffix[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.suffix "Permalink to this definition")

The suffix appended at the end of every page. e.g. three backticks, if any.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

max_size[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.max_size "Permalink to this definition")

The maximum amount of codepoints allowed in a page.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

linesep[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.linesep "Permalink to this definition")

The character string inserted between lines. e.g. a newline character.

New in version 1.7.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

clear()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.clear "Permalink to this definition")

Clears the paginator to have no pages.

add_line(_line=''_, _*_, _empty=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.add_line "Permalink to this definition")

Adds a line to the current page.

If the line exceeds the [`max_size`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.max_size "discord.ext.commands.Paginator.max_size") then an exception is raised.

Parameters

*   **line** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The line to add.
    
*   **empty** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates if another empty line should be added.
    

Raises

[**RuntimeError**](https://docs.python.org/3/library/exceptions.html#RuntimeError "(in Python v3.13)") – The line was too big for the current [`max_size`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.max_size "discord.ext.commands.Paginator.max_size").

close_page()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.close_page "Permalink to this definition")

Prematurely terminate a page.

_property_ pages[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Paginator.pages "Permalink to this definition")

Returns the rendered list of pages.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

## Enums[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#enums "Permalink to this headline")

_class_ discord.ext.commands.BucketType[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "Permalink to this definition")

Specifies a type of bucket for, e.g. a cooldown.

default[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.default "Permalink to this definition")

The default bucket operates on a global basis.

user[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.user "Permalink to this definition")

The user bucket operates on a per-user basis.

guild[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.guild "Permalink to this definition")

The guild bucket operates on a per-guild basis.

channel[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.channel "Permalink to this definition")

The channel bucket operates on a per-channel basis.

member[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.member "Permalink to this definition")

The member bucket operates on a per-member basis.

category[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.category "Permalink to this definition")

The category bucket operates on a per-category basis.

role[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType.role "Permalink to this definition")

The role bucket operates on a per-role basis.

New in version 1.3.

## Checks[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#checks "Permalink to this headline")

@discord.ext.commands.check(_predicate_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "Permalink to this definition")

A decorator that adds a check to the [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") or its subclasses. These checks could be accessed via [`Command.checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks").

These checks should be predicates that take in a single parameter taking a [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context"). If the check returns a `False`-like value then during invocation a [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure") exception is raised and sent to the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event.

If an exception should be thrown in the predicate then it should be a subclass of [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError"). Any exception not subclassed from it will be propagated while those subclassed will be sent to [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error").

A special attribute named `predicate` is bound to the value returned by this decorator to retrieve the predicate passed to the decorator. This allows the following introspection and chaining to be done:

content_copy

```
def owner_or_permissions(**perms):
    original = commands.has_permissions(**perms).predicate
    async def extended_check(ctx):
        if ctx.guild is None:
            return False
        return ctx.guild.owner_id == ctx.author.id or await original(ctx)
    return commands.check(extended_check)
```

Note

The function returned by `predicate` is **always** a coroutine, even if the original function was not a coroutine.

Changed in version 1.3: The `predicate` attribute was added.

Examples

Creating a basic check to see if the command invoker is you.

content_copy

```
def check_if_it_is_me(ctx):
    return ctx.message.author.id == 85309593344815104

@bot.command()
@commands.check(check_if_it_is_me)
async def only_for_me(ctx):
    await ctx.send('I know you!')
```

Transforming common checks into its own decorator:

content_copy

```
def is_me():
    def predicate(ctx):
        return ctx.message.author.id == 85309593344815104
    return commands.check(predicate)

@bot.command()
@is_me()
async def only_me(ctx):
    await ctx.send('Only you!')
```

Changed in version 2.0: `predicate` parameter is now positional-only.

Parameters

**predicate** (Callable[[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")], [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – The predicate to check if the command should be invoked.

@discord.ext.commands.check_any(_*checks_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check_any "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that is added that checks if any of the checks passed will pass, i.e. using logical OR.

If all checks fail then [`CheckAnyFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckAnyFailure "discord.ext.commands.CheckAnyFailure") is raised to signal the failure. It inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

Note

The `predicate` attribute for this function **is** a coroutine.

New in version 1.3.

Parameters

***checks** (Callable[[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")], [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – An argument list of checks that have been decorated with the [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") decorator.

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – A check passed has not been decorated with the [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") decorator.

Examples

Creating a basic check to see if it’s the bot owner or the server owner:

content_copy

```
def is_guild_owner():
    def predicate(ctx):
        return ctx.guild is not None and ctx.guild.owner_id == ctx.author.id
    return commands.check(predicate)

@bot.command()
@commands.check_any(commands.is_owner(), is_guild_owner())
async def only_for_owners(ctx):
    await ctx.send('Hello mister owner!')
```

@discord.ext.commands.has_role(_item_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_role "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that is added that checks if the member invoking the command has the role specified via the name or ID specified.

If a string is specified, you must give the exact name of the role, including caps and spelling.

If an integer is specified, you must give the exact snowflake ID of the role.

If the message is invoked in a private message context then the check will return `False`.

This check raises one of two special exceptions, [`MissingRole`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRole "discord.ext.commands.MissingRole") if the user is missing a role, or [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") if it is used in a private message. Both inherit from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

Changed in version 2.0: `item` parameter is now positional-only.

Parameters

**item** (Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The name or ID of the role to check.

@discord.ext.commands.has_permissions(_**perms_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_permissions "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that is added that checks if the member has all of the permissions necessary.

Note that this check operates on the current channel permissions, not the guild wide permissions.

The permissions passed in must be exactly like the properties shown under [`discord.Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions").

This check raises a special exception, [`MissingPermissions`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingPermissions "discord.ext.commands.MissingPermissions") that is inherited from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

Parameters

**perms** – An argument list of permissions to check for.

Example

content_copy

```
@bot.command()
@commands.has_permissions(manage_messages=True)
async def test(ctx):
    await ctx.send('You can manage messages.')
```

@discord.ext.commands.has_guild_permissions(_**perms_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_guild_permissions "Permalink to this definition")

Similar to [`has_permissions()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_permissions "discord.ext.commands.has_permissions"), but operates on guild wide permissions instead of the current channel permissions.

If this check is called in a DM context, it will raise an exception, [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage").

New in version 1.3.

@discord.ext.commands.has_any_role(_*items_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_any_role "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that is added that checks if the member invoking the command has **any** of the roles specified. This means that if they have one out of the three roles specified, then this check will return `True`.

Similar to [`has_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_role "discord.ext.commands.has_role"), the names or IDs passed in must be exact.

This check raises one of two special exceptions, [`MissingAnyRole`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingAnyRole "discord.ext.commands.MissingAnyRole") if the user is missing all roles, or [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") if it is used in a private message. Both inherit from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

Parameters

**items** (List[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]) – An argument list of names or IDs to check that the member has roles wise.

Example

content_copy

```
@bot.command()
@commands.has_any_role('Library Devs', 'Moderators', 492212595072434186)
async def cool(ctx):
    await ctx.send('You are cool indeed')
```

@discord.ext.commands.bot_has_role(_item_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.bot_has_role "Permalink to this definition")

Similar to [`has_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_role "discord.ext.commands.has_role") except checks if the bot itself has the role.

This check raises one of two special exceptions, [`BotMissingRole`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingRole "discord.ext.commands.BotMissingRole") if the bot is missing the role, or [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") if it is used in a private message. Both inherit from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

Changed in version 2.0: `item` parameter is now positional-only.

@discord.ext.commands.bot_has_permissions(_**perms_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.bot_has_permissions "Permalink to this definition")

Similar to [`has_permissions()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_permissions "discord.ext.commands.has_permissions") except checks if the bot itself has the permissions listed.

This check raises a special exception, [`BotMissingPermissions`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingPermissions "discord.ext.commands.BotMissingPermissions") that is inherited from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

@discord.ext.commands.bot_has_guild_permissions(_**perms_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.bot_has_guild_permissions "Permalink to this definition")

Similar to [`has_guild_permissions()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_guild_permissions "discord.ext.commands.has_guild_permissions"), but checks the bot members guild permissions.

New in version 1.3.

@discord.ext.commands.bot_has_any_role(_*items_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.bot_has_any_role "Permalink to this definition")

Similar to [`has_any_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_any_role "discord.ext.commands.has_any_role") except checks if the bot itself has any of the roles listed.

This check raises one of two special exceptions, [`BotMissingAnyRole`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingAnyRole "discord.ext.commands.BotMissingAnyRole") if the bot is missing all roles, or [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") if it is used in a private message. Both inherit from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

@discord.ext.commands.cooldown(_rate_, _per_, _type=discord.ext.commands.BucketType.default_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.cooldown "Permalink to this definition")

A decorator that adds a cooldown to a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")

A cooldown allows a command to only be used a specific amount of times in a specific time frame. These cooldowns can be based either on a per-guild, per-channel, per-user, per-role or global basis. Denoted by the third argument of `type` which must be of enum type [`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType").

If a cooldown is triggered, then [`CommandOnCooldown`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandOnCooldown "discord.ext.commands.CommandOnCooldown") is triggered in [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") and the local error handler.

A command can only have a single cooldown.

Parameters

*   **rate** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The number of times a command can be used before triggering a cooldown.
    
*   **per** ([`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")) – The amount of seconds to wait for a cooldown when it’s been triggered.
    
*   **type** (Union[[`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType"), Callable[[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")], Any]]) –
    
    The type of cooldown to have. If callable, should return a key for the mapping.
    
    Changed in version 1.7: Callables are now supported for custom bucket types.
    
    Changed in version 2.0: When passing a callable, it now needs to accept [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") rather than [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") as its only argument.
    

@discord.ext.commands.dynamic_cooldown(_cooldown_, _type_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.dynamic_cooldown "Permalink to this definition")

A decorator that adds a dynamic cooldown to a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")

This differs from [`cooldown()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.cooldown "discord.ext.commands.cooldown") in that it takes a function that accepts a single parameter of type [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") and must return a [`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown") or `None`. If `None` is returned then that cooldown is effectively bypassed.

A cooldown allows a command to only be used a specific amount of times in a specific time frame. These cooldowns can be based either on a per-guild, per-channel, per-user, per-role or global basis. Denoted by the third argument of `type` which must be of enum type [`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType").

If a cooldown is triggered, then [`CommandOnCooldown`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandOnCooldown "discord.ext.commands.CommandOnCooldown") is triggered in [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") and the local error handler.

A command can only have a single cooldown.

New in version 2.0.

Parameters

*   **cooldown** (Callable[[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")], Optional[[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")]]) – A function that takes a message and returns a cooldown that will apply to this invocation or `None` if the cooldown should be bypassed.
    
*   **type** ([`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType")) – The type of cooldown to have.
    

@discord.ext.commands.max_concurrency(_number_, _per=discord.ext.commands.BucketType.default_, _*_, _wait=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.max_concurrency "Permalink to this definition")

A decorator that adds a maximum concurrency to a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") or its subclasses.

This enables you to only allow a certain number of command invocations at the same time, for example if a command takes too long or if only one user can use it at a time. This differs from a cooldown in that there is no set waiting period or token bucket – only a set number of people can run the command.

New in version 1.3.

Parameters

*   **number** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The maximum number of invocations of this command that can be running at the same time.
    
*   **per** ([`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType")) – The bucket that this concurrency is based on, e.g. `BucketType.guild` would allow it to be used up to `number` times per guild.
    
*   **wait** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether the command should wait for the queue to be over. If this is set to `False` then instead of waiting until the command can run again, the command raises [`MaxConcurrencyReached`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MaxConcurrencyReached "discord.ext.commands.MaxConcurrencyReached") to its error handler. If this is set to `True` then the command waits until it can be executed.
    

@discord.ext.commands.before_invoke(_coro_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.before_invoke "Permalink to this definition")

A decorator that registers a coroutine as a pre-invoke hook.

This allows you to refer to one before invoke hook for several commands that do not have to be within the same cog.

New in version 1.4.

Changed in version 2.0: `coro` parameter is now positional-only.

Example

content_copy

```
async def record_usage(ctx):
    print(ctx.author, 'used', ctx.command, 'at', ctx.message.created_at)

@bot.command()
@commands.before_invoke(record_usage)
async def who(ctx): # Output: <User> used who at <Time>
    await ctx.send('i am a bot')

class What(commands.Cog):

 @commands.before_invoke(record_usage)
 @commands.command()
    async def when(self, ctx): # Output: <User> used when at <Time>
        await ctx.send(f'and i have existed since {ctx.bot.user.created_at}')

 @commands.command()
    async def where(self, ctx): # Output: <Nothing>
        await ctx.send('on Discord')

 @commands.command()
    async def why(self, ctx): # Output: <Nothing>
        await ctx.send('because someone made me')
```

@discord.ext.commands.after_invoke(_coro_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.after_invoke "Permalink to this definition")

A decorator that registers a coroutine as a post-invoke hook.

This allows you to refer to one after invoke hook for several commands that do not have to be within the same cog.

New in version 1.4.

Changed in version 2.0: `coro` parameter is now positional-only.

@discord.ext.commands.guild_only()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.guild_only "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that indicates this command must only be used in a guild context only. Basically, no private messages are allowed when using the command.

This check raises a special exception, [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") that is inherited from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

If used on hybrid commands, this will be equivalent to the [`discord.app_commands.guild_only()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.guild_only "discord.app_commands.guild_only") decorator. In an unsupported context, such as a subcommand, this will still fallback to applying the check.

@discord.ext.commands.dm_only()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.dm_only "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that indicates this command must only be used in a DM context. Only private messages are allowed when using the command.

This check raises a special exception, [`PrivateMessageOnly`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PrivateMessageOnly "discord.ext.commands.PrivateMessageOnly") that is inherited from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

New in version 1.1.

@discord.ext.commands.is_owner()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.is_owner "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that checks if the person invoking this command is the owner of the bot.

This is powered by [`Bot.is_owner()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.is_owner "discord.ext.commands.Bot.is_owner").

This check raises a special exception, [`NotOwner`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NotOwner "discord.ext.commands.NotOwner") that is derived from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

@discord.ext.commands.is_nsfw()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.is_nsfw "Permalink to this definition")

A [`check()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check "discord.ext.commands.check") that checks if the channel is a NSFW channel.

This check raises a special exception, [`NSFWChannelRequired`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NSFWChannelRequired "discord.ext.commands.NSFWChannelRequired") that is derived from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

If used on hybrid commands, this will be equivalent to setting the application command’s `nsfw` attribute to `True`. In an unsupported context, such as a subcommand, this will still fallback to applying the check.

Changed in version 1.1: Raise [`NSFWChannelRequired`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NSFWChannelRequired "discord.ext.commands.NSFWChannelRequired") instead of generic [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure"). DM channels will also now pass this check.

## Context[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#context "Permalink to this headline")

_class_ discord.ext.commands.Context(_*_, _message_, _bot_, _view_, _args=..._, _kwargs=..._, _prefix=None_, _command=None_, _invoked_with=None_, _invoked_parents=..._, _invoked_subcommand=None_, _subcommand_passed=None_, _command_failed=False_, _current_parameter=None_, _current_argument=None_, _interaction=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "Permalink to this definition")

Represents the context in which a command is being invoked under.

This class contains a lot of meta data to help you understand more about the invocation context. This class is not created manually and is instead passed around to commands as the first parameter.

This class implements the [`Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable") ABC.

message[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.message "Permalink to this definition")

The message that triggered the command being executed.

Note

In the case of an interaction based context, this message is “synthetic” and does not actually exist. Therefore, the ID on it is invalid similar to ephemeral messages.

Type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

bot[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.bot "Permalink to this definition")

The bot that contains the command being executed.

Type

[`Bot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot "discord.ext.commands.Bot")

args[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.args "Permalink to this definition")

The list of transformed arguments that were passed into the command. If this is accessed during the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event then this list could be incomplete.

Type

[`list`](https://docs.python.org/3/library/stdtypes.html#list "(in Python v3.13)")

kwargs[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.kwargs "Permalink to this definition")

A dictionary of transformed arguments that were passed into the command. Similar to [`args`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.args "discord.ext.commands.Context.args"), if this is accessed in the [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error") event then this dict could be incomplete.

Type

[`dict`](https://docs.python.org/3/library/stdtypes.html#dict "(in Python v3.13)")

current_parameter[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.current_parameter "Permalink to this definition")

The parameter that is currently being inspected and converted. This is only of use for within converters.

New in version 2.0.

Type

Optional[[`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")]

current_argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.current_argument "Permalink to this definition")

The argument string of the [`current_parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.current_parameter "discord.ext.commands.Context.current_parameter") that is currently being converted. This is only of use for within converters.

New in version 2.0.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

interaction[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.interaction "Permalink to this definition")

The interaction associated with this context.

New in version 2.0.

Type

Optional[[`Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")]

prefix[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.prefix "Permalink to this definition")

The prefix that was used to invoke the command. For interaction based contexts, this is `/` for slash commands and `\u200b` for context menu commands.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

command[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.command "Permalink to this definition")

The command that is being invoked currently.

Type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

invoked_with[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoked_with "Permalink to this definition")

The command name that triggered this invocation. Useful for finding out which alias called the command.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

invoked_parents[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoked_parents "Permalink to this definition")

The command names of the parents that triggered this invocation. Useful for finding out which aliases called the command.

For example in commands `?a b c test`, the invoked parents are `['a', 'b', 'c']`.

New in version 1.7.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

invoked_subcommand[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoked_subcommand "Permalink to this definition")

The subcommand that was invoked. If no valid subcommand was invoked then this is equal to `None`.

Type

Optional[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")]

subcommand_passed[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.subcommand_passed "Permalink to this definition")

The string that was attempted to call a subcommand. This does not have to point to a valid registered subcommand and could just point to a nonsense string. If nothing was passed to attempt a call to a subcommand then this is set to `None`.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

command_failed[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.command_failed "Permalink to this definition")

A boolean that indicates if the command failed to be parsed, checked, or invoked.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_async with_ typing(_*_, _ephemeral=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.typing "Permalink to this definition")

Returns an asynchronous context manager that allows you to send a typing indicator to the destination for an indefinite period of time, or 10 seconds if the context manager is called using `await`.

In an interaction based context, this is equivalent to a [`defer()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.defer "discord.ext.commands.Context.defer") call and does not do any typing calls.

Example Usage:

content_copy

```
async with channel.typing():
    # simulate something heavy
    await asyncio.sleep(20)

await channel.send('Done!')
```

Example Usage:

content_copy

```
await channel.typing()
# Do some computational magic for about 10 seconds
await channel.send('Done!')
```

Changed in version 2.0: This no longer works with the `with` syntax, `async with` must be used instead.

Changed in version 2.0: Added functionality to `await` the context manager to send a typing indicator for 10 seconds.

Parameters

**ephemeral** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –

Indicates whether the deferred message will eventually be ephemeral. Only valid for interaction based contexts.

New in version 2.0.

_classmethod await_ from_interaction(_interaction_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.from_interaction "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Creates a context from a [`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction"). This only works on application command based interactions, such as slash commands or context menus.

On slash command based interactions this creates a synthetic [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") that points to an ephemeral message that the command invoker has executed. This means that [`Context.author`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.author "discord.ext.commands.Context.author") returns the member that invoked the command.

In a message context menu based interaction, the [`Context.message`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.message "discord.ext.commands.Context.message") attribute is the message that the command is being executed on. This means that [`Context.author`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.author "discord.ext.commands.Context.author") returns the author of the message being targetted. To get the member that invoked the command then [`discord.Interaction.user`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.user "discord.Interaction.user") should be used instead.

New in version 2.0.

Parameters

**interaction** ([`discord.Interaction`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction "discord.Interaction")) – The interaction to create a context with.

Raises

*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The interaction does not have a valid command.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The interaction client is not derived from [`Bot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot "discord.ext.commands.Bot") or [`AutoShardedBot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.AutoShardedBot "discord.ext.commands.AutoShardedBot").
    

_await_ invoke(_command_, _/_, _*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoke "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Calls a command with the arguments given.

This is useful if you want to just call the callback that a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command") holds internally.

Note

This does not handle converters, checks, cooldowns, pre-invoke, or after-invoke hooks in any matter. It calls the internal callback directly as-if it was a regular function.

You must take care in passing the proper arguments when using this function.

Changed in version 2.0: `command` parameter is now positional-only.

Parameters

*   **command** ([`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")) – The command that is going to be called.
    
*   ***args** – The arguments to use.
    
*   ****kwargs** – The keyword arguments to use.
    

Raises

[**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – The command argument to invoke is missing.

_await_ reinvoke(_*_, _call_hooks=False_, _restart=True_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.reinvoke "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Calls the command again.

This is similar to [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoke "discord.ext.commands.Context.invoke") except that it bypasses checks, cooldowns, and error handlers.

Note

If you want to bypass [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError") derived exceptions, it is recommended to use the regular [`invoke()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.invoke "discord.ext.commands.Context.invoke") as it will work more naturally. After all, this will end up using the old arguments the user has used and will thus just fail again.

Parameters

*   **call_hooks** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to call the before and after invoke hooks.
    
*   **restart** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether to start the call chain from the very beginning or where we left off (i.e. the command that caused the error). The default is to start where we left off.
    

Raises

[**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The context to reinvoke is not valid.

_property_ valid[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.valid "Permalink to this definition")

Checks if the invocation context is valid to be invoked with.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ clean_prefix[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.clean_prefix "Permalink to this definition")

The cleaned up invoke prefix. i.e. mentions are `@name` instead of `<@id>`.

New in version 2.0.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_property_ cog[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.cog "Permalink to this definition")

Returns the cog associated with this context’s command. None if it does not exist.

Type

Optional[[`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog")]

_property_ filesize_limit[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.filesize_limit "Permalink to this definition")

Returns the maximum number of bytes files can have when uploaded to this guild or DM channel associated with this context.

New in version 2.3.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

guild[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.guild "Permalink to this definition")

Returns the guild associated with this context’s command. None if not available.

Type

Optional[[`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild")]

channel[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.channel "Permalink to this definition")

Returns the channel associated with this context’s command. Shorthand for [`Message.channel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.channel "discord.Message.channel").

Type

Union[[`abc.Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable")]

Union[[`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User"), [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member")]: Returns the author associated with this context’s command. Shorthand for [`Message.author`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.author "discord.Message.author")

me[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.me "Permalink to this definition")

Union[[`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member"), [`ClientUser`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientUser "discord.ClientUser")]: Similar to [`Guild.me`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild.me "discord.Guild.me") except it may return the [`ClientUser`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientUser "discord.ClientUser") in private message contexts.

permissions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.permissions "Permalink to this definition")

Returns the resolved permissions for the invoking user in this channel. Shorthand for [`abc.GuildChannel.permissions_for()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel.permissions_for "discord.abc.GuildChannel.permissions_for") or [`Interaction.permissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.permissions "discord.Interaction.permissions").

New in version 2.0.

Type

[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")

bot_permissions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.bot_permissions "Permalink to this definition")

Returns the resolved permissions for the bot in this channel. Shorthand for [`abc.GuildChannel.permissions_for()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel.permissions_for "discord.abc.GuildChannel.permissions_for") or [`Interaction.app_permissions`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.Interaction.app_permissions "discord.Interaction.app_permissions").

For interaction-based commands, this will reflect the effective permissions for [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") calls, which may differ from calls through other [`abc.Messageable`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable "discord.abc.Messageable") endpoints, like [`channel`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.channel "discord.ext.commands.Context.channel").

Notably, sending messages, embedding links, and attaching files are always permitted, while reading messages might not be.

New in version 2.0.

Type

[`Permissions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions "discord.Permissions")

_property_ voice_client[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.voice_client "Permalink to this definition")

A shortcut to [`Guild.voice_client`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild.voice_client "discord.Guild.voice_client"), if applicable.

Type

Optional[[`VoiceProtocol`](https://discordpy.readthedocs.io/en/stable/api.html#discord.VoiceProtocol "discord.VoiceProtocol")]

_await_ send_help(_entity=<bot>_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.send_help "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Shows the help command for the specified entity if given. The entity can be a command or a cog.

If no entity is given, then it’ll show help for the entire bot.

If the entity is a string, then it looks up whether it’s a [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog") or a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command").

Note

Due to the way this function works, instead of returning something similar to [`command_not_found()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HelpCommand.command_not_found "discord.ext.commands.HelpCommand.command_not_found") this returns `None` on bad input or no help command.

Parameters

**entity** (Optional[Union[[`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command"), [`Cog`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Cog "discord.ext.commands.Cog"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]]) – The entity to show help for.

Returns

The result of the help command, if any.

Return type

Any

_await_ fetch_message(_id_, _/_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.fetch_message "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Retrieves a single [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") from the destination.

Parameters

**id** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The message ID to look for.

Raises

*   [**NotFound**](https://discordpy.readthedocs.io/en/stable/api.html#discord.NotFound "discord.NotFound") – The specified message was not found.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the permissions required to get a message.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the message failed.
    

Returns

The message asked for.

Return type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

_async for ... in_ history(_*_, _limit=100_, _before=None_, _after=None_, _around=None_, _oldest_first=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.history "Permalink to this definition")

Returns an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator "(in Python v3.13)") that enables receiving the destination’s message history.

You must have [`read_message_history`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.read_message_history "discord.Permissions.read_message_history") to do this.

Examples

Usage

content_copy

```
counter = 0
async for message in channel.history(limit=200):
    if message.author == client.user:
        counter += 1
```

Flattening into a list:

content_copy

```
messages = [message async for message in channel.history(limit=123)]
# messages is now a list of Message...
```

All parameters are optional.

Parameters

*   **limit** (Optional[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]) – The number of messages to retrieve. If `None`, retrieves every message in the channel. Note, however, that this would make it a slow operation.
    
*   **before** (Optional[Union[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]]) – Retrieve messages before this date or message. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
*   **after** (Optional[Union[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]]) – Retrieve messages after this date or message. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
*   **around** (Optional[Union[[`Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake"), [`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)")]]) – Retrieve messages around this date or message. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time. When using this argument, the maximum limit is 101. Note that if the limit is an even number then this will return at most limit + 1 messages.
    
*   **oldest_first** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) – If set to `True`, return messages in oldest->newest order. Defaults to `True` if `after` is specified, otherwise `False`.
    

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have permissions to get channel message history.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – The request to get message history failed.
    

Yields

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") – The message with the message data parsed.

pins(_*_, _limit=50_, _before=None_, _oldest_first=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.pins "Permalink to this definition")

Retrieves an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator "(in Python v3.13)") of the pinned messages in the channel.

You must have [`view_channel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.view_channel "discord.Permissions.view_channel") and [`read_message_history`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Permissions.read_message_history "discord.Permissions.read_message_history") in order to use this.

Changed in version 2.6: Due to a change in Discord’s API, this now returns a paginated iterator instead of a list.

For backwards compatibility, you can still retrieve a list of pinned messages by using `await` on the returned object. This is however deprecated.

Note

Due to a limitation with the Discord API, the [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") object returned by this method does not contain complete [`Message.reactions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.reactions "discord.Message.reactions") data.

Examples

Usage

content_copy

```
counter = 0
async for message in channel.pins(limit=250):
    counter += 1
```

Flattening into a list:

content_copy

```
messages = [message async for message in channel.pins(limit=50)]
# messages is now a list of Message...
```

All parameters are optional.

Parameters

*   **limit** (_Optional__[_[_int_](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")_]_) –
    
    The number of pinned messages to retrieve. If `None`, it retrieves every pinned message in the channel. Note, however, that this would make it a slow operation. Defaults to `50`.
    
    New in version 2.6.
    
*   **before** (Optional[Union[[`datetime.datetime`](https://docs.python.org/3/library/datetime.html#datetime.datetime "(in Python v3.13)"), [`abc.Snowflake`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Snowflake "discord.abc.Snowflake")]]) –
    
    Retrieve pinned messages before this time or snowflake. If a datetime is provided, it is recommended to use a UTC aware datetime. If the datetime is naive, it is assumed to be local time.
    
    New in version 2.6.
    
*   **oldest_first** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    If set to `True`, return messages in oldest pin->newest pin order. Defaults to `False`.
    
    New in version 2.6.
    

Raises

*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the permission to retrieve pinned messages.
    
*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Retrieving the pinned messages failed.
    

Yields

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") – The pinned message with [`Message.pinned_at`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.pinned_at "discord.Message.pinned_at") set.

_await_ reply(_content=None_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.reply "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

A shortcut method to [`send()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.send "discord.ext.commands.Context.send") to reply to the [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") referenced by this context.

For interaction based contexts, this is the same as [`send()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.send "discord.ext.commands.Context.send").

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

_await_ defer(_*_, _ephemeral=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.defer "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Defers the interaction based contexts.

This is typically used when the interaction is acknowledged and a secondary action will be done later.

If this isn’t an interaction based context then it does nothing.

Parameters

**ephemeral** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates whether the deferred message will eventually be ephemeral.

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Deferring the interaction failed.
    
*   [**InteractionResponded**](https://discordpy.readthedocs.io/en/stable/api.html#discord.InteractionResponded "discord.InteractionResponded") – This interaction has already been responded to before.
    

_await_ send(_content=None_, _*_, _tts=False_, _embed=None_, _embeds=None_, _file=None_, _files=None_, _stickers=None_, _delete_after=None_, _nonce=None_, _allowed_mentions=None_, _reference=None_, _mention_author=None_, _view=None_, _suppress_embeds=False_, _ephemeral=False_, _silent=False_, _poll=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.send "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Sends a message to the destination with the content given.

This works similarly to [`send()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.Messageable.send "discord.abc.Messageable.send") for non-interaction contexts.

For interaction based contexts this does one of the following:

*   [`discord.InteractionResponse.send_message()`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.InteractionResponse.send_message "discord.InteractionResponse.send_message") if no response has been given.
    
*   A followup message if a response has been given.
    
*   Regular send if the interaction has expired
    

Changed in version 2.0: This function will now raise [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") or [`ValueError`](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") instead of `InvalidArgument`.

Parameters

*   **content** (Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – The content of the message to send.
    
*   **tts** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Indicates if the message should be sent using text-to-speech.
    
*   **embed** ([`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")) – The rich embed for the content.
    
*   **file** ([`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")) – The file to upload.
    
*   **files** (List[[`File`](https://discordpy.readthedocs.io/en/stable/api.html#discord.File "discord.File")]) – A list of files to upload. Must be a maximum of 10.
    
*   **nonce** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The nonce to use for sending this message. If the message was successfully sent, then the message will have a nonce with this value.
    
*   **delete_after** ([`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")) – If provided, the number of seconds to wait in the background before deleting the message we just sent. If the deletion fails, then it is silently ignored.
    
*   **allowed_mentions** ([`AllowedMentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions "discord.AllowedMentions")) –
    
    Controls the mentions being processed in this message. If this is passed, then the object is merged with [`allowed_mentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.allowed_mentions "discord.Client.allowed_mentions"). The merging behaviour only overrides attributes that have been explicitly passed to the object, otherwise it uses the attributes set in [`allowed_mentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.allowed_mentions "discord.Client.allowed_mentions"). If no object is passed at all then the defaults given by [`allowed_mentions`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Client.allowed_mentions "discord.Client.allowed_mentions") are used instead.
    
    New in version 1.4.
    
*   **reference** (Union[[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message"), [`MessageReference`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageReference "discord.MessageReference"), [`PartialMessage`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialMessage "discord.PartialMessage")]) –
    
    A reference to the [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message") to which you are replying, this can be created using [`to_reference()`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.to_reference "discord.Message.to_reference") or passed directly as a [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message"). You can control whether this mentions the author of the referenced message using the [`replied_user`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions.replied_user "discord.AllowedMentions.replied_user") attribute of `allowed_mentions` or by setting `mention_author`.
    
    This is ignored for interaction based contexts.
    
    New in version 1.6.
    
*   **mention_author** (Optional[[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]) –
    
    If set, overrides the [`replied_user`](https://discordpy.readthedocs.io/en/stable/api.html#discord.AllowedMentions.replied_user "discord.AllowedMentions.replied_user") attribute of `allowed_mentions`. This is ignored for interaction based contexts.
    
    New in version 1.6.
    
*   **view** (Union[[`discord.ui.View`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.View "discord.ui.View"), [`discord.ui.LayoutView`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.ui.LayoutView "discord.ui.LayoutView")]) –
    
    A Discord UI View to add to the message.
    
    New in version 2.0.
    
*   **embeds** (List[[`Embed`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Embed "discord.Embed")]) –
    
    A list of embeds to upload. Must be a maximum of 10.
    
    New in version 2.0.
    
*   **stickers** (Sequence[Union[[`GuildSticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.GuildSticker "discord.GuildSticker"), [`StickerItem`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StickerItem "discord.StickerItem")]]) –
    
    A list of stickers to upload. Must be a maximum of 3. This is ignored for interaction based contexts.
    
    New in version 2.0.
    
*   **suppress_embeds** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to suppress embeds for the message. This sends the message without any embeds if set to `True`.
    
    New in version 2.0.
    
*   **ephemeral** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Indicates if the message should only be visible to the user who started the interaction. If a view is sent with an ephemeral message and it has no timeout set then the timeout is set to 15 minutes. **This is only applicable in contexts with an interaction**.
    
    New in version 2.0.
    
*   **silent** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether to suppress push and desktop notifications for the message. This will increment the mention counter in the UI, but will not actually send a notification.
    
    New in version 2.2.
    
*   **poll** (Optional[[`Poll`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Poll "discord.Poll")]) –
    
    The poll to send with this message.
    
    New in version 2.4.
    
    Changed in version 2.6: This can now be `None` and defaults to `None` instead of `MISSING`.
    

Raises

*   [**HTTPException**](https://discordpy.readthedocs.io/en/stable/api.html#discord.HTTPException "discord.HTTPException") – Sending the message failed.
    
*   [**Forbidden**](https://discordpy.readthedocs.io/en/stable/api.html#discord.Forbidden "discord.Forbidden") – You do not have the proper permissions to send the message.
    
*   [**ValueError**](https://docs.python.org/3/library/exceptions.html#ValueError "(in Python v3.13)") – The `files` list is not of the appropriate size.
    
*   [**TypeError**](https://docs.python.org/3/library/exceptions.html#TypeError "(in Python v3.13)") – You specified both `file` and `files`, or you specified both `embed` and `embeds`, or the `reference` object is not a [`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message"), [`MessageReference`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MessageReference "discord.MessageReference") or [`PartialMessage`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialMessage "discord.PartialMessage").
    

Returns

The message that was sent.

Return type

[`Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message")

## Converters[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#converters "Permalink to this headline")

_class_ discord.ext.commands.Converter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Converter "Permalink to this definition")

The base class of custom converters that require the [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") to be passed to be useful.

This allows you to implement converters that function similar to the special cased `discord` classes.

Classes that derive from this should override the [`convert()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Converter.convert "discord.ext.commands.Converter.convert") method to do its conversion logic. This method must be a [coroutine](https://docs.python.org/3/library/asyncio-task.html#coroutine "(in Python v3.13)").

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Converter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.ObjectConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ObjectConverter "Permalink to this definition")

Converts to a [`Object`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Object "discord.Object").

The argument must follow the valid ID or mention formats (e.g. `<@80088516616269824>`).

New in version 2.0.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by member, role, or channel mention.
    

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ObjectConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.MemberConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MemberConverter "Permalink to this definition")

Converts to a [`Member`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Member "discord.Member").

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by username#discriminator (deprecated).
    
4.  Lookup by username#0 (deprecated, only gets users that migrated from their discriminator).
    
5.  Lookup by user name.
    
6.  Lookup by global name.
    
7.  Lookup by guild nickname.
    

Changed in version 1.5.1: This converter now lazily fetches members from the gateway and HTTP APIs, optionally caching the result if [`MemberCacheFlags.joined`](https://discordpy.readthedocs.io/en/stable/api.html#discord.MemberCacheFlags.joined "discord.MemberCacheFlags.joined") is enabled.

Deprecated since version 2.3: Looking up users by discriminator will be removed in a future version due to the removal of discriminators in an API change.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MemberConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.UserConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserConverter "Permalink to this definition")

Converts to a [`User`](https://discordpy.readthedocs.io/en/stable/api.html#discord.User "discord.User").

All lookups are via the global user cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by username#discriminator (deprecated).
    
4.  Lookup by username#0 (deprecated, only gets users that migrated from their discriminator).
    
5.  Lookup by user name.
    
6.  Lookup by global name.
    

Changed in version 1.6: This converter now lazily fetches users from the HTTP APIs if an ID is passed and it’s not available in cache.

Deprecated since version 2.3: Looking up users by discriminator will be removed in a future version due to the removal of discriminators in an API change.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.MessageConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MessageConverter "Permalink to this definition")

Converts to a [`discord.Message`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message "discord.Message").

New in version 1.1.

The lookup strategy is as follows (in order):

1.  Lookup by “{channel ID}-{message ID}” (retrieved by shift-clicking on “Copy ID”)
    
2.  Lookup by message ID (the message **must** be in the context channel)
    
3.  Lookup by message URL
    

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MessageConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.PartialMessageConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PartialMessageConverter "Permalink to this definition")

Converts to a [`discord.PartialMessage`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialMessage "discord.PartialMessage").

New in version 1.7.

The creation strategy is as follows (in order):

1.  By “{channel ID}-{message ID}” (retrieved by shift-clicking on “Copy ID”)
    
2.  By message ID (The message is assumed to be in the context channel.)
    
3.  By message URL
    

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PartialMessageConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.GuildChannelConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildChannelConverter "Permalink to this definition")

Converts to a [`GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel").

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name.
    

New in version 2.0.

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildChannelConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.TextChannelConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TextChannelConverter "Permalink to this definition")

Converts to a [`TextChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.TextChannel "discord.TextChannel").

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name
    

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TextChannelConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.VoiceChannelConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.VoiceChannelConverter "Permalink to this definition")

Converts to a [`VoiceChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.VoiceChannel "discord.VoiceChannel").

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name
    

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.VoiceChannelConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.StageChannelConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.StageChannelConverter "Permalink to this definition")

Converts to a [`StageChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.StageChannel "discord.StageChannel").

New in version 1.7.

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name
    

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.StageChannelConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.CategoryChannelConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CategoryChannelConverter "Permalink to this definition")

Converts to a [`CategoryChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.CategoryChannel "discord.CategoryChannel").

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name
    

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CategoryChannelConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.ForumChannelConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ForumChannelConverter "Permalink to this definition")

Converts to a [`ForumChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ForumChannel "discord.ForumChannel").

All lookups are via the local guild. If in a DM context, then the lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name
    

New in version 2.0.

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ForumChannelConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.InviteConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.InviteConverter "Permalink to this definition")

Converts to a [`Invite`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Invite "discord.Invite").

This is done via an HTTP request using [`Bot.fetch_invite()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot.fetch_invite "discord.ext.commands.Bot.fetch_invite").

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.InviteConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.GuildConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildConverter "Permalink to this definition")

Converts to a [`Guild`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Guild "discord.Guild").

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by name. (There is no disambiguation for Guilds with multiple matching names).
    

New in version 1.7.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.RoleConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RoleConverter "Permalink to this definition")

Converts to a [`Role`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Role "discord.Role").

All lookups are via the local guild. If in a DM context, the converter raises [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") exception.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by name
    

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RoleConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.GameConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GameConverter "Permalink to this definition")

Converts to a [`Game`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Game "discord.Game").

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GameConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.ColourConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ColourConverter "Permalink to this definition")

Converts to a [`Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour").

Changed in version 1.5: Add an alias named ColorConverter

The following formats are accepted:

*   `0x<hex>`
    
*   `#<hex>`
    
*   `0x#<hex>`
    
*   `rgb(<number>, <number>, <number>)`
    
*   Any of the `classmethod` in [`Colour`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Colour "discord.Colour")
    
    *   The `_` in the name can be optionally replaced with spaces.
        
    

Like CSS, `<number>` can be either 0-255 or 0-100% and `<hex>` can be either a 6 digit hex number or a 3 digit hex shortcut (e.g. #fff).

Changed in version 1.7: Added support for `rgb` function and 3-digit hex shortcuts

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ColourConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.EmojiConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.EmojiConverter "Permalink to this definition")

Converts to a [`Emoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Emoji "discord.Emoji").

All lookups are done for the local guild first, if available. If that lookup fails, then it checks the client’s global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by extracting ID from the emoji.
    
3.  Lookup by name
    

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.EmojiConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.PartialEmojiConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PartialEmojiConverter "Permalink to this definition")

Converts to a [`PartialEmoji`](https://discordpy.readthedocs.io/en/stable/api.html#discord.PartialEmoji "discord.PartialEmoji").

This is done by extracting the animated flag, name and ID from the emoji.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PartialEmojiConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.ThreadConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ThreadConverter "Permalink to this definition")

Converts to a [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread").

All lookups are via the local guild.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by mention.
    
3.  Lookup by channel URL.
    
4.  Lookup by name.
    

Changed in version 2.4: Add lookup by channel URL, accessed via “Copy Link” in the Discord client within channels.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ThreadConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.GuildStickerConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildStickerConverter "Permalink to this definition")

Converts to a [`GuildSticker`](https://discordpy.readthedocs.io/en/stable/api.html#discord.GuildSticker "discord.GuildSticker").

All lookups are done for the local guild first, if available. If that lookup fails, then it checks the client’s global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by name.
    

New in version 2.0.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildStickerConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.ScheduledEventConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ScheduledEventConverter "Permalink to this definition")

Converts to a [`ScheduledEvent`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ScheduledEvent "discord.ScheduledEvent").

Lookups are done for the local guild if available. Otherwise, for a DM context, lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by url.
    
3.  Lookup by name.
    

New in version 2.0.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ScheduledEventConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.SoundboardSoundConverter(_*args_, _**kwargs_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.SoundboardSoundConverter "Permalink to this definition")

Converts to a [`SoundboardSound`](https://discordpy.readthedocs.io/en/stable/api.html#discord.SoundboardSound "discord.SoundboardSound").

Lookups are done for the local guild if available. Otherwise, for a DM context, lookup is done by the global cache.

The lookup strategy is as follows (in order):

1.  Lookup by ID.
    
2.  Lookup by name.
    

New in version 2.5.

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.SoundboardSoundConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.clean_content(_*_, _fix_channel_mentions=False_, _use_nicknames=True_, _escape_markdown=False_, _remove_markdown=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.clean_content "Permalink to this definition")

Converts the argument to mention scrubbed version of said content.

This behaves similarly to [`clean_content`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Message.clean_content "discord.Message.clean_content").

fix_channel_mentions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.clean_content.fix_channel_mentions "Permalink to this definition")

Whether to clean channel mentions.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

use_nicknames[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.clean_content.use_nicknames "Permalink to this definition")

Whether to use nicknames when transforming mentions.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

escape_markdown[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.clean_content.escape_markdown "Permalink to this definition")

Whether to also escape special markdown characters.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

remove_markdown[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.clean_content.remove_markdown "Permalink to this definition")

Whether to also remove special markdown characters. This option is not supported with `escape_markdown`

New in version 1.7.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.clean_content.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method to override to do conversion logic.

If an error is found while converting, it is recommended to raise a [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") derived exception as it will properly propagate to the error handlers.

Note that if this method is called manually, [`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)") should be caught to handle the cases where a subclass does not explicitly inherit from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that the argument is being used in.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument that is being converted.
    

Raises

*   [**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – A generic exception occurred when converting the argument.
    
*   [**BadArgument**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") – The converter failed to convert the argument.
    

_class_ discord.ext.commands.Greedy[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Greedy "Permalink to this definition")

A special converter that greedily consumes arguments until it can’t. As a consequence of this behaviour, most input errors are silently discarded, since it is used as an indicator of when to stop parsing.

When a parser error is met the greedy converter stops converting, undoes the internal string parsing routine, and continues parsing regularly.

For example, in the following code:

content_copy

```
@commands.command()
async def test(ctx, numbers: Greedy[int], reason: str):
    await ctx.send("numbers: {}, reason: {}".format(numbers, reason))
```

An invocation of `[p]test 1 2 3 4 5 6 hello` would pass `numbers` with `[1, 2, 3, 4, 5, 6]` and `reason` with `hello`.

For more information, check [Special Converters](https://discordpy.readthedocs.io/en/stable/ext/commands/commands.html#ext-commands-special-converters).

Note

For interaction based contexts the conversion error is propagated rather than swallowed due to the difference in user experience with application commands.

_class_ discord.ext.commands.Range[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Range "Permalink to this definition")

A special converter that can be applied to a parameter to require a numeric or string type to fit within the range provided.

During type checking time this is equivalent to [`typing.Annotated`](https://docs.python.org/3/library/typing.html#typing.Annotated "(in Python v3.13)") so type checkers understand the intent of the code.

Some example ranges:

*   `Range[int, 10]` means the minimum is 10 with no maximum.
    
*   `Range[int, None, 10]` means the maximum is 10 with no minimum.
    
*   `Range[int, 1, 10]` means the minimum is 1 and the maximum is 10.
    
*   `Range[float, 1.0, 5.0]` means the minimum is 1.0 and the maximum is 5.0.
    
*   `Range[str, 1, 10]` means the minimum length is 1 and the maximum length is 10.
    

Inside a [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand") this functions equivalently to [`discord.app_commands.Range`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Range "discord.app_commands.Range").

If the value cannot be converted to the provided type or is outside the given range, [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument") or [`RangeError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RangeError "discord.ext.commands.RangeError") is raised to the appropriate error handlers respectively.

New in version 2.0.

Examples

content_copy

```
@bot.command()
async def range(ctx: commands.Context, value: commands.Range[int, 10, 12]):
    await ctx.send(f'Your value is {value}')
```

_await_ discord.ext.commands.run_converters(_ctx_, _converter_, _argument_, _param_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.run_converters "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Runs converters for a given converter, argument, and parameter.

This function does the same work that the library does under the hood.

New in version 2.0.

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context to run the converters under.
    
*   **converter** (_Any_) – The converter to run, this corresponds to the annotation in the function.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument to convert to.
    
*   **param** ([`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")) – The parameter being converted. This is mainly for error reporting.
    

Raises

[**CommandError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") – The converter failed to convert.

Returns

The resulting conversion.

Return type

Any

### Flag Converter[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#flag-converter "Permalink to this headline")

_class_ discord.ext.commands.FlagConverter[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagConverter "Permalink to this definition")

A converter that allows for a user-friendly flag syntax.

The flags are defined using [**PEP 526**](https://www.python.org/dev/peps/pep-0526) type annotations similar to the [`dataclasses`](https://docs.python.org/3/library/dataclasses.html#module-dataclasses "(in Python v3.13)") Python module. For more information on how this converter works, check the appropriate [documentation](https://discordpy.readthedocs.io/en/stable/ext/commands/commands.html#ext-commands-flag-converter).

iter(x)

Returns an iterator of `(flag_name, flag_value)` pairs. This allows it to be, for example, constructed as a dict or a list of pairs. Note that aliases are not shown.

New in version 2.0.

Parameters

*   **case_insensitive** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – A class parameter to toggle case insensitivity of the flag parsing. If `True` then flags are parsed in a case insensitive manner. Defaults to `False`.
    
*   **prefix** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The prefix that all flags must be prefixed with. By default there is no prefix.
    
*   **delimiter** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The delimiter that separates a flag’s argument from the flag’s name. By default this is `:`.
    

_classmethod_ get_flags()[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagConverter.get_flags "Permalink to this definition")

Dict[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`Flag`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag "discord.ext.commands.Flag")]: A mapping of flag name to flag object this converter has.

_classmethod await_ convert(_ctx_, _argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagConverter.convert "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

The method that actually converters an argument to the flag mapping.

Parameters

*   **ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context.
    
*   **argument** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The argument to convert from.
    

Raises

[**FlagError**](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagError "discord.ext.commands.FlagError") – A flag related parsing error.

Returns

The flag converter instance with all flags parsed.

Return type

[`FlagConverter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagConverter "discord.ext.commands.FlagConverter")

_class_ discord.ext.commands.Flag[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag "Permalink to this definition")

Represents a flag parameter for [`FlagConverter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagConverter "discord.ext.commands.FlagConverter").

The [`flag()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.flag "discord.ext.commands.flag") function helps create these flag objects, but it is not necessary to do so. These cannot be constructed manually.

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.name "Permalink to this definition")

The name of the flag.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

aliases[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.aliases "Permalink to this definition")

The aliases of the flag name.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

attribute[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.attribute "Permalink to this definition")

The attribute in the class that corresponds to this flag.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

default[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.default "Permalink to this definition")

The default value of the flag, if available.

Type

Any

annotation[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.annotation "Permalink to this definition")

The underlying evaluated annotation of the flag.

Type

Any

max_args[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.max_args "Permalink to this definition")

The maximum number of arguments the flag can accept. A negative value indicates an unlimited amount of arguments.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

override[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.override "Permalink to this definition")

Whether multiple given values overrides the previous value.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.description "Permalink to this definition")

The description of the flag. Shown for hybrid commands when they’re used as application commands.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

positional[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.positional "Permalink to this definition")

Whether the flag is positional or not. There can only be one positional flag.

New in version 2.4.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ required[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag.required "Permalink to this definition")

Whether the flag is required.

A required flag has no default value.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

discord.ext.commands.flag(_*_, _name=..._, _aliases=..._, _default=..._, _max_args=..._, _override=..._, _converter=..._, _description=..._, _positional=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.flag "Permalink to this definition")

Override default functionality and parameters of the underlying [`FlagConverter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagConverter "discord.ext.commands.FlagConverter") class attributes.

Parameters

*   **name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The flag name. If not given, defaults to the attribute name.
    
*   **aliases** (List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]) – Aliases to the flag name. If not given no aliases are set.
    
*   **default** (_Any_) – The default parameter. This could be either a value or a callable that takes [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") as its sole parameter. If not given then it defaults to the default value given to the attribute.
    
*   **max_args** ([`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")) – The maximum number of arguments the flag can accept. A negative value indicates an unlimited amount of arguments. The default value depends on the annotation given.
    
*   **override** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) – Whether multiple given values overrides the previous value. The default value depends on the annotation given.
    
*   **converter** (_Any_) – The converter to use for this flag. This replaces the annotation at runtime which is transparent to type checkers.
    
*   **description** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The description of the flag. Shown for hybrid commands when they’re used as application commands.
    
*   **positional** ([`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")) –
    
    Whether the flag is positional or not. There can only be one positional flag.
    
    New in version 2.4.
    

## Defaults[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#defaults "Permalink to this headline")

_class_ discord.ext.commands.Parameter[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "Permalink to this definition")

A class that stores information on a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")'s parameter.

This is a subclass of [`inspect.Parameter`](https://docs.python.org/3/library/inspect.html#inspect.Parameter "(in Python v3.13)").

New in version 2.0.

replace(_*_, _name=..._, _kind=..._, _default=..._, _annotation=..._, _description=..._, _displayed_default=..._, _displayed_name=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.replace "Permalink to this definition")

Creates a customized copy of the Parameter.

_property_ name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.name "Permalink to this definition")

The parameter’s name.

_property_ kind[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.kind "Permalink to this definition")

The parameter’s kind.

_property_ default[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.default "Permalink to this definition")

The parameter’s default.

_property_ annotation[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.annotation "Permalink to this definition")

The parameter’s annotation.

_property_ required[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.required "Permalink to this definition")

Whether this parameter is required.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_property_ converter[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.converter "Permalink to this definition")

The converter that should be used for this parameter.

_property_ description[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.description "Permalink to this definition")

The description of this parameter.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ displayed_default[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.displayed_default "Permalink to this definition")

The displayed default in [`Command.signature`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.signature "discord.ext.commands.Command.signature").

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_property_ displayed_name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.displayed_name "Permalink to this definition")

The name that is displayed to the user.

New in version 2.3.

Type

Optional[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_await_ get_default(_ctx_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter.get_default "Permalink to this definition")

This function is a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine).

Gets this parameter’s default value.

Parameters

**ctx** ([`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")) – The invocation context that is used to get the default argument.

discord.ext.commands.parameter(_\*_, _converter=..._, _default=..._, _description=..._, _displayed_default=..._, _displayed_name=..._)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.parameter "Permalink to this definition")

A way to assign custom metadata for a [`Command`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command "discord.ext.commands.Command")'s parameter.

New in version 2.0.

Examples

A custom default can be used to have late binding behaviour.

content_copy

```
@bot.command()
async def wave(ctx, to: discord.User = commands.parameter(default=lambda ctx: ctx.author)):
    await ctx.send(f'Hello {to.mention} :wave:')
```

Parameters

*   **converter** (_Any_) – The converter to use for this parameter, this replaces the annotation at runtime which is transparent to type checkers.
    
*   **default** (_Any_) – The default value for the parameter, if this is a [callable](https://docs.python.org/3/glossary.html#term-callable "(in Python v3.13)") or a [_coroutine_](https://docs.python.org/3/library/asyncio-task.html#coroutine) it is called with a positional [`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context") argument.
    
*   **description** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The description of this parameter.
    
*   **displayed_default** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) – The displayed default in [`Command.signature`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.signature "discord.ext.commands.Command.signature").
    
*   **displayed_name** ([`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")) –
    
    The name that is displayed to the user.
    
    New in version 2.3.
    

discord.ext.commands.param(_*_, _converter_, _default_, _description_, _displayed_default_, _displayed_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.param "Permalink to this definition")

param(*, converter=…, default=…, description=…, displayed_default=…, displayed_name=…)

An alias for [`parameter()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.parameter "discord.ext.commands.parameter").

New in version 2.0.

discord.ext.commands.Author[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.Author "Permalink to this definition")

A default [`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter") which returns the [`author`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.author "discord.ext.commands.Context.author") for this context.

New in version 2.0.

discord.ext.commands.CurrentChannel[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.CurrentChannel "Permalink to this definition")

A default [`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter") which returns the [`channel`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.channel "discord.ext.commands.Context.channel") for this context.

New in version 2.0.

discord.ext.commands.CurrentGuild[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.CurrentGuild "Permalink to this definition")

A default [`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter") which returns the [`guild`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context.guild "discord.ext.commands.Context.guild") for this context. This will never be `None`. If the command is called in a DM context then [`NoPrivateMessage`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "discord.ext.commands.NoPrivateMessage") is raised to the error handlers.

New in version 2.0.

## Exceptions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#exceptions "Permalink to this headline")

_exception_ discord.ext.commands.CommandError(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "Permalink to this definition")

The base exception type for all command related errors.

This inherits from [`discord.DiscordException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.DiscordException "discord.DiscordException").

This exception and exceptions inherited from it are handled in a special way as they are caught and passed into a special event from [`Bot`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Bot "discord.ext.commands.Bot"), [`on_command_error()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.discord.ext.commands.on_command_error "discord.discord.ext.commands.on_command_error").

_exception_ discord.ext.commands.ConversionError(_converter_, _original_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ConversionError "Permalink to this definition")

Exception raised when a Converter class raises non-CommandError.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

converter[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ConversionError.converter "Permalink to this definition")

The converter that failed.

Type

[`discord.ext.commands.Converter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Converter "discord.ext.commands.Converter")

original[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ConversionError.original "Permalink to this definition")

The original exception that was raised. You can also get this via the `__cause__` attribute.

Type

[`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")

_exception_ discord.ext.commands.MissingRequiredArgument(_param_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredArgument "Permalink to this definition")

Exception raised when parsing a command and a parameter that is required is not encountered.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError")

param[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredArgument.param "Permalink to this definition")

The argument that is missing.

Type

[`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")

_exception_ discord.ext.commands.MissingRequiredAttachment(_param_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredAttachment "Permalink to this definition")

Exception raised when parsing a command and a parameter that requires an attachment is not given.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError")

New in version 2.0.

param[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredAttachment.param "Permalink to this definition")

The argument that is missing an attachment.

Type

[`Parameter`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Parameter "discord.ext.commands.Parameter")

_exception_ discord.ext.commands.ArgumentParsingError(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ArgumentParsingError "Permalink to this definition")

An exception raised when the parser fails to parse a user’s input.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError").

There are child classes that implement more granular parsing errors for i18n purposes.

_exception_ discord.ext.commands.UnexpectedQuoteError(_quote_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UnexpectedQuoteError "Permalink to this definition")

An exception raised when the parser encounters a quote mark inside a non-quoted string.

This inherits from [`ArgumentParsingError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ArgumentParsingError "discord.ext.commands.ArgumentParsingError").

quote[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UnexpectedQuoteError.quote "Permalink to this definition")

The quote mark that was found inside the non-quoted string.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.InvalidEndOfQuotedStringError(_char_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.InvalidEndOfQuotedStringError "Permalink to this definition")

An exception raised when a space is expected after the closing quote in a string but a different character is found.

This inherits from [`ArgumentParsingError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ArgumentParsingError "discord.ext.commands.ArgumentParsingError").

char[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.InvalidEndOfQuotedStringError.char "Permalink to this definition")

The character found instead of the expected string.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.ExpectedClosingQuoteError(_close_quote_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExpectedClosingQuoteError "Permalink to this definition")

An exception raised when a quote character is expected but not found.

This inherits from [`ArgumentParsingError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ArgumentParsingError "discord.ext.commands.ArgumentParsingError").

close_quote[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExpectedClosingQuoteError.close_quote "Permalink to this definition")

The quote character expected.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.BadArgument(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "Permalink to this definition")

Exception raised when a parsing or conversion failure is encountered on an argument to pass into a command.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError")

_exception_ discord.ext.commands.BadUnionArgument(_param_, _converters_, _errors_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadUnionArgument "Permalink to this definition")

Exception raised when a [`typing.Union`](https://docs.python.org/3/library/typing.html#typing.Union "(in Python v3.13)") converter fails for all its associated types.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError")

param[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadUnionArgument.param "Permalink to this definition")

The parameter that failed being converted.

Type

[`inspect.Parameter`](https://docs.python.org/3/library/inspect.html#inspect.Parameter "(in Python v3.13)")

converters[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadUnionArgument.converters "Permalink to this definition")

A tuple of converters attempted in conversion, in order of failure.

Type

Tuple[Type, `...`]

errors[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadUnionArgument.errors "Permalink to this definition")

A list of errors that were caught from failing the conversion.

Type

List[[`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")]

_exception_ discord.ext.commands.BadLiteralArgument(_param_, _literals_, _errors_, _argument=''_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadLiteralArgument "Permalink to this definition")

Exception raised when a [`typing.Literal`](https://docs.python.org/3/library/typing.html#typing.Literal "(in Python v3.13)") converter fails for all its associated values.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError")

New in version 2.0.

param[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadLiteralArgument.param "Permalink to this definition")

The parameter that failed being converted.

Type

[`inspect.Parameter`](https://docs.python.org/3/library/inspect.html#inspect.Parameter "(in Python v3.13)")

literals[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadLiteralArgument.literals "Permalink to this definition")

A tuple of values compared against in conversion, in order of failure.

Type

Tuple[Any, `...`]

errors[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadLiteralArgument.errors "Permalink to this definition")

A list of errors that were caught from failing the conversion.

Type

List[[`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")]

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadLiteralArgument.argument "Permalink to this definition")

The argument’s value that failed to be converted. Defaults to an empty string.

New in version 2.3.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.PrivateMessageOnly(_message=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PrivateMessageOnly "Permalink to this definition")

Exception raised when an operation does not work outside of private message contexts.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

_exception_ discord.ext.commands.NoPrivateMessage(_message=None_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoPrivateMessage "Permalink to this definition")

Exception raised when an operation does not work in private message contexts.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

_exception_ discord.ext.commands.CheckFailure(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "Permalink to this definition")

Exception raised when the predicates in [`Command.checks`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.checks "discord.ext.commands.Command.checks") have failed.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")

_exception_ discord.ext.commands.CheckAnyFailure(_checks_, _errors_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckAnyFailure "Permalink to this definition")

Exception raised when all predicates in [`check_any()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.check_any "discord.ext.commands.check_any") fail.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

New in version 1.3.

errors[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckAnyFailure.errors "Permalink to this definition")

A list of errors that were caught during execution.

Type

List[[`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")]

checks[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckAnyFailure.checks "Permalink to this definition")

A list of check predicates that failed.

Type

List[Callable[[[`Context`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Context "discord.ext.commands.Context")], [`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")]]

_exception_ discord.ext.commands.CommandNotFound(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandNotFound "Permalink to this definition")

Exception raised when a command is attempted to be invoked but no command under that name is found.

This is not raised for invalid subcommands, rather just the initial main command that is attempted to be invoked.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

_exception_ discord.ext.commands.DisabledCommand(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.DisabledCommand "Permalink to this definition")

Exception raised when the command being invoked is disabled.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")

_exception_ discord.ext.commands.CommandInvokeError(_e_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandInvokeError "Permalink to this definition")

Exception raised when the command being invoked raised an exception.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")

original[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandInvokeError.original "Permalink to this definition")

The original exception that was raised. You can also get this via the `__cause__` attribute.

Type

[`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")

_exception_ discord.ext.commands.TooManyArguments(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TooManyArguments "Permalink to this definition")

Exception raised when the command was passed too many arguments and its [`Command.ignore_extra`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Command.ignore_extra "discord.ext.commands.Command.ignore_extra") attribute was not set to `True`.

This inherits from [`UserInputError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "discord.ext.commands.UserInputError")

_exception_ discord.ext.commands.UserInputError(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserInputError "Permalink to this definition")

The base exception type for errors that involve errors regarding user input.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

_exception_ discord.ext.commands.CommandOnCooldown(_cooldown_, _retry_after_, _type_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandOnCooldown "Permalink to this definition")

Exception raised when the command being invoked is on cooldown.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError")

cooldown[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandOnCooldown.cooldown "Permalink to this definition")

A class with attributes `rate` and `per` similar to the [`cooldown()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.cooldown "discord.ext.commands.cooldown") decorator.

Type

[`Cooldown`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.Cooldown "discord.app_commands.Cooldown")

type[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandOnCooldown.type "Permalink to this definition")

The type associated with the cooldown.

Type

[`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType")

retry_after[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandOnCooldown.retry_after "Permalink to this definition")

The amount of seconds to wait before you can retry again.

Type

[`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")

_exception_ discord.ext.commands.MaxConcurrencyReached(_number_, _per_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MaxConcurrencyReached "Permalink to this definition")

Exception raised when the command being invoked has reached its maximum concurrency.

This inherits from [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError").

number[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MaxConcurrencyReached.number "Permalink to this definition")

The maximum number of concurrent invokers allowed.

Type

[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")

per[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MaxConcurrencyReached.per "Permalink to this definition")

The bucket type passed to the [`max_concurrency()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.max_concurrency "discord.ext.commands.max_concurrency") decorator.

Type

[`BucketType`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BucketType "discord.ext.commands.BucketType")

_exception_ discord.ext.commands.NotOwner(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NotOwner "Permalink to this definition")

Exception raised when the message author is not the owner of the bot.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

_exception_ discord.ext.commands.MessageNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MessageNotFound "Permalink to this definition")

Exception raised when the message provided was not found in the channel.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MessageNotFound.argument "Permalink to this definition")

The message supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.MemberNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MemberNotFound "Permalink to this definition")

Exception raised when the member provided was not found in the bot’s cache.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MemberNotFound.argument "Permalink to this definition")

The member supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.GuildNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildNotFound "Permalink to this definition")

Exception raised when the guild provided was not found in the bot’s cache.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.7.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildNotFound.argument "Permalink to this definition")

The guild supplied by the called that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.UserNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserNotFound "Permalink to this definition")

Exception raised when the user provided was not found in the bot’s cache.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.UserNotFound.argument "Permalink to this definition")

The user supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.ChannelNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ChannelNotFound "Permalink to this definition")

Exception raised when the bot can not find the channel.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ChannelNotFound.argument "Permalink to this definition")

The channel supplied by the caller that was not found

Type

Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.ext.commands.ChannelNotReadable(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ChannelNotReadable "Permalink to this definition")

Exception raised when the bot does not have permission to read messages in the channel.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ChannelNotReadable.argument "Permalink to this definition")

The channel supplied by the caller that was not readable

Type

Union[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel"), [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")]

_exception_ discord.ext.commands.ThreadNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ThreadNotFound "Permalink to this definition")

Exception raised when the bot can not find the thread.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 2.0.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ThreadNotFound.argument "Permalink to this definition")

The thread supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.BadColourArgument(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadColourArgument "Permalink to this definition")

Exception raised when the colour is not valid.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadColourArgument.argument "Permalink to this definition")

The colour supplied by the caller that was not valid

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.RoleNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RoleNotFound "Permalink to this definition")

Exception raised when the bot can not find the role.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RoleNotFound.argument "Permalink to this definition")

The role supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.BadInviteArgument(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadInviteArgument "Permalink to this definition")

Exception raised when the invite is invalid or expired.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadInviteArgument.argument "Permalink to this definition")

The invite supplied by the caller that was not valid

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.EmojiNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.EmojiNotFound "Permalink to this definition")

Exception raised when the bot can not find the emoji.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.EmojiNotFound.argument "Permalink to this definition")

The emoji supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.PartialEmojiConversionFailure(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PartialEmojiConversionFailure "Permalink to this definition")

Exception raised when the emoji provided does not match the correct format.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.PartialEmojiConversionFailure.argument "Permalink to this definition")

The emoji supplied by the caller that did not match the regex

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.GuildStickerNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildStickerNotFound "Permalink to this definition")

Exception raised when the bot can not find the sticker.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 2.0.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.GuildStickerNotFound.argument "Permalink to this definition")

The sticker supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.ScheduledEventNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ScheduledEventNotFound "Permalink to this definition")

Exception raised when the bot can not find the scheduled event.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 2.0.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ScheduledEventNotFound.argument "Permalink to this definition")

The event supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.SoundboardSoundNotFound(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.SoundboardSoundNotFound "Permalink to this definition")

Exception raised when the bot can not find the soundboard sound.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 2.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.SoundboardSoundNotFound.argument "Permalink to this definition")

The sound supplied by the caller that was not found

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.BadBoolArgument(_argument_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadBoolArgument "Permalink to this definition")

Exception raised when a boolean argument was not convertable.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 1.5.

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadBoolArgument.argument "Permalink to this definition")

The boolean argument supplied by the caller that is not in the predefined list

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.RangeError(_value_, _minimum_, _maximum_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RangeError "Permalink to this definition")

Exception raised when an argument is out of range.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument")

New in version 2.0.

minimum[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RangeError.minimum "Permalink to this definition")

The minimum value expected or `None` if there wasn’t one

Type

Optional[Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]]

maximum[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RangeError.maximum "Permalink to this definition")

The maximum value expected or `None` if there wasn’t one

Type

Optional[Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)")]]

value[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.RangeError.value "Permalink to this definition")

The value that was out of range.

Type

Union[[`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)"), [`float`](https://docs.python.org/3/library/functions.html#float "(in Python v3.13)"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.ext.commands.MissingPermissions(_missing_permissions_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingPermissions "Permalink to this definition")

Exception raised when the command invoker lacks permissions to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

missing_permissions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingPermissions.missing_permissions "Permalink to this definition")

The required permissions that are missing.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.ext.commands.BotMissingPermissions(_missing_permissions_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingPermissions "Permalink to this definition")

Exception raised when the bot’s member lacks permissions to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

missing_permissions[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingPermissions.missing_permissions "Permalink to this definition")

The required permissions that are missing.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.ext.commands.MissingRole(_missing_role_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRole "Permalink to this definition")

Exception raised when the command invoker lacks a role to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

New in version 1.1.

missing_role[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRole.missing_role "Permalink to this definition")

The required role that is missing. This is the parameter passed to [`has_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_role "discord.ext.commands.has_role").

Type

Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_exception_ discord.ext.commands.BotMissingRole(_missing_role_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingRole "Permalink to this definition")

Exception raised when the bot’s member lacks a role to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

New in version 1.1.

missing_role[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingRole.missing_role "Permalink to this definition")

The required role that is missing. This is the parameter passed to [`has_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_role "discord.ext.commands.has_role").

Type

Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]

_exception_ discord.ext.commands.MissingAnyRole(_missing_roles_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingAnyRole "Permalink to this definition")

Exception raised when the command invoker lacks any of the roles specified to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

New in version 1.1.

missing_roles[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingAnyRole.missing_roles "Permalink to this definition")

The roles that the invoker is missing. These are the parameters passed to [`has_any_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_any_role "discord.ext.commands.has_any_role").

Type

List[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]

_exception_ discord.ext.commands.BotMissingAnyRole(_missing_roles_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingAnyRole "Permalink to this definition")

Exception raised when the bot’s member lacks any of the roles specified to run a command.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure")

New in version 1.1.

missing_roles[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BotMissingAnyRole.missing_roles "Permalink to this definition")

The roles that the bot’s member is missing. These are the parameters passed to [`has_any_role()`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.has_any_role "discord.ext.commands.has_any_role").

Type

List[Union[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)"), [`int`](https://docs.python.org/3/library/functions.html#int "(in Python v3.13)")]]

_exception_ discord.ext.commands.NSFWChannelRequired(_channel_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NSFWChannelRequired "Permalink to this definition")

Exception raised when a channel does not have the required NSFW setting.

This inherits from [`CheckFailure`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CheckFailure "discord.ext.commands.CheckFailure").

New in version 1.1.

channel[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NSFWChannelRequired.channel "Permalink to this definition")

The channel that does not have NSFW enabled.

Type

Union[[`abc.GuildChannel`](https://discordpy.readthedocs.io/en/stable/api.html#discord.abc.GuildChannel "discord.abc.GuildChannel"), [`Thread`](https://discordpy.readthedocs.io/en/stable/api.html#discord.Thread "discord.Thread")]

_exception_ discord.ext.commands.FlagError(_message=None_, _*args_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagError "Permalink to this definition")

The base exception type for all flag parsing related errors.

This inherits from [`BadArgument`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadArgument "discord.ext.commands.BadArgument").

New in version 2.0.

_exception_ discord.ext.commands.BadFlagArgument(_flag_, _argument_, _original_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadFlagArgument "Permalink to this definition")

An exception raised when a flag failed to convert a value.

This inherits from [`FlagError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagError "discord.ext.commands.FlagError")

New in version 2.0.

flag[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadFlagArgument.flag "Permalink to this definition")

The flag that failed to convert.

Type

[`Flag`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag "discord.ext.commands.Flag")

argument[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadFlagArgument.argument "Permalink to this definition")

The argument supplied by the caller that was not able to be converted.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

original[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.BadFlagArgument.original "Permalink to this definition")

The original exception that was raised. You can also get this via the `__cause__` attribute.

Type

[`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")

_exception_ discord.ext.commands.MissingFlagArgument(_flag_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingFlagArgument "Permalink to this definition")

An exception raised when a flag did not get a value.

This inherits from [`FlagError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagError "discord.ext.commands.FlagError")

New in version 2.0.

flag[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingFlagArgument.flag "Permalink to this definition")

The flag that did not get a value.

Type

[`Flag`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag "discord.ext.commands.Flag")

_exception_ discord.ext.commands.TooManyFlags(_flag_, _values_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TooManyFlags "Permalink to this definition")

An exception raised when a flag has received too many values.

This inherits from [`FlagError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagError "discord.ext.commands.FlagError").

New in version 2.0.

flag[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TooManyFlags.flag "Permalink to this definition")

The flag that received too many values.

Type

[`Flag`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag "discord.ext.commands.Flag")

values[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.TooManyFlags.values "Permalink to this definition")

The values that were passed.

Type

List[[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")]

_exception_ discord.ext.commands.MissingRequiredFlag(_flag_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredFlag "Permalink to this definition")

An exception raised when a required flag was not given.

This inherits from [`FlagError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.FlagError "discord.ext.commands.FlagError")

New in version 2.0.

flag[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.MissingRequiredFlag.flag "Permalink to this definition")

The required flag that was not found.

Type

[`Flag`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.Flag "discord.ext.commands.Flag")

_exception_ discord.ext.commands.ExtensionError(_message=None_, _*args_, _name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError "Permalink to this definition")

Base exception for extension related errors.

This inherits from [`DiscordException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.DiscordException "discord.DiscordException").

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError.name "Permalink to this definition")

The extension that had an error.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.ExtensionAlreadyLoaded(_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionAlreadyLoaded "Permalink to this definition")

An exception raised when an extension has already been loaded.

This inherits from [`ExtensionError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError "discord.ext.commands.ExtensionError")

_exception_ discord.ext.commands.ExtensionNotLoaded(_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotLoaded "Permalink to this definition")

An exception raised when an extension was not loaded.

This inherits from [`ExtensionError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError "discord.ext.commands.ExtensionError")

_exception_ discord.ext.commands.NoEntryPointError(_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.NoEntryPointError "Permalink to this definition")

An exception raised when an extension does not have a `setup` entry point function.

This inherits from [`ExtensionError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError "discord.ext.commands.ExtensionError")

_exception_ discord.ext.commands.ExtensionFailed(_name_, _original_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionFailed "Permalink to this definition")

An exception raised when an extension failed to load during execution of the module or `setup` entry point.

This inherits from [`ExtensionError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError "discord.ext.commands.ExtensionError")

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionFailed.name "Permalink to this definition")

The extension that had the error.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

original[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionFailed.original "Permalink to this definition")

The original exception that was raised. You can also get this via the `__cause__` attribute.

Type

[`Exception`](https://docs.python.org/3/library/exceptions.html#Exception "(in Python v3.13)")

_exception_ discord.ext.commands.ExtensionNotFound(_name_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotFound "Permalink to this definition")

An exception raised when an extension is not found.

This inherits from [`ExtensionError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionError "discord.ext.commands.ExtensionError")

Changed in version 1.3: Made the `original` attribute always None.

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.ExtensionNotFound.name "Permalink to this definition")

The extension that had the error.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

_exception_ discord.ext.commands.CommandRegistrationError(_name_, _*_, _alias_conflict=False_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError "Permalink to this definition")

An exception raised when the command can’t be added because the name is already taken by a different command.

This inherits from [`discord.ClientException`](https://discordpy.readthedocs.io/en/stable/api.html#discord.ClientException "discord.ClientException")

New in version 1.4.

name[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError.name "Permalink to this definition")

The command name that had the error.

Type

[`str`](https://docs.python.org/3/library/stdtypes.html#str "(in Python v3.13)")

alias_conflict[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandRegistrationError.alias_conflict "Permalink to this definition")

Whether the name that conflicts is an alias of the command we try to add.

Type

[`bool`](https://docs.python.org/3/library/functions.html#bool "(in Python v3.13)")

_exception_ discord.ext.commands.HybridCommandError(_original_)[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommandError "Permalink to this definition")

An exception raised when a [`HybridCommand`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommand "discord.ext.commands.HybridCommand") raises an [`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError") derived exception that could not be sufficiently converted to an equivalent [`CommandError`](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.CommandError "discord.ext.commands.CommandError") exception.

New in version 2.0.

original[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#discord.ext.commands.HybridCommandError.original "Permalink to this definition")

The original exception that was raised. You can also get this via the `__cause__` attribute.

Type

[`AppCommandError`](https://discordpy.readthedocs.io/en/stable/interactions/api.html#discord.app_commands.AppCommandError "discord.app_commands.AppCommandError")

### Exception Hierarchy[¶](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html#exception-hierarchy "Permalink to this headline")