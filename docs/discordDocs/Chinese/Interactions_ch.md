
当用户使用应用命令或消息组件时，[交互](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object)就是您的应用程序接收到的消息。

对于[斜杠命令](https://discord.com/developers/docs/interactions/application-commands#slash-commands)，它包含用户提交的值。

对于[用户命令](https://discord.com/developers/docs/interactions/application-commands#user-commands)和[消息命令](https://discord.com/developers/docs/interactions/application-commands#message-commands)，它包含执行操作时解析出的用户或消息。

对于[消息组件](https://discord.com/developers/docs/components/reference)，它包含有关所使用组件的标识信息。它还将包含有关交互触发方式的一些元数据：`guild_id`、`channel`、`member` 和其他字段。您可以在下面的数据模型中查找所有值。

### [交互对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object)

###### [交互结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-structure)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>id</td><td>雪花ID</td><td>交互的唯一标识符</td></tr><tr><td>application_id</td><td>雪花ID</td><td>此交互所属应用的ID</td></tr><tr><td>type</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type" data-discover="true">交互类型</a></td><td>交互的类型</td></tr><tr><td>data?*</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-data" data-discover="true">交互数据</a></td><td>交互数据负载</td></tr><tr><td>guild?</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">部分服务器</a>对象</td><td>交互发送来源的服务器</td></tr><tr><td>guild_id?</td><td>雪花ID</td><td>交互发送来源的服务器ID</td></tr><tr><td>channel?</td><td><a href="https://discord.com/developers/docs/resources/channel#channel-object" data-discover="true">部分频道</a>对象</td><td>交互发送来源的频道</td></tr><tr><td>channel_id?</td><td>雪花ID</td><td>交互发送来源的频道ID</td></tr><tr><td>member?**</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">服务器成员</a>对象</td><td>调用用户的服务器成员数据，包括权限</td></tr><tr><td>user?</td><td><a href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">用户</a>对象</td><td>如果在私信中调用，则为调用用户的用户对象</td></tr><tr><td>token</td><td>字符串</td><td>用于响应交互的续传令牌</td></tr><tr><td>version</td><td>整数</td><td>只读属性，始终为<code>1</code></td></tr><tr><td>message?</td><td><a href="https://discord.com/developers/docs/resources/message#message-object" data-discover="true">消息</a>对象</td><td>对于由组件触发的组件或模态框，它们所附加的消息</td></tr><tr><td>app_permissions***</td><td>字符串</td><td>应用在交互源位置拥有的权限位集</td></tr><tr><td>locale?****</td><td>字符串</td><td>调用用户选择的<a href="https://discord.com/developers/docs/reference#locales" data-discover="true">语言</a></td></tr><tr><td>guild_locale?</td><td>字符串</td><td>如果在服务器中调用，则为<a href="https://discord.com/developers/docs/resources/guild#guild-object" data-discover="true">服务器的首选语言</a></td></tr><tr><td>entitlements</td><td><a href="https://discord.com/developers/docs/resources/entitlement#entitlement-object" data-discover="true">授权</a>对象数组</td><td>对于<a href="https://discord.com/developers/docs/monetization/overview" data-discover="true">商业化应用</a>，调用用户的任何授权，代表对高级<a href="https://discord.com/developers/docs/resources/sku" data-discover="true">SKU</a>的访问权限</td></tr><tr><td>authorizing_integration_owners</td><td>以<a href="https://discord.com/developers/docs/resources/application#application-object-application-integration-types" data-discover="true">应用集成类型</a>为键的字典</td><td>交互被授权安装的上下文映射到相关用户或服务器ID。详情参见<a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-authorizing-integration-owners-object" data-discover="true">授权集成所有者对象</a></td></tr><tr><td>context?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-context-types" data-discover="true">交互上下文类型</a></td><td>交互触发的上下文</td></tr><tr><td>attachment_size_limit</td><td>整数</td><td>附件大小限制（字节）</td></tr></tbody></table>

`*` : 该字段始终存在于应用命令、消息组件和模态提交交互类型中。为面向未来兼容新交互类型，该字段为可选

`**` : 当交互在服务器中调用时发送 `member`，在私信（DM）中调用时发送 `user`

`***` : `app_permissions` 包含与其他用户的（群组）私信中的 `ATTACH_FILES | EMBED_LINKS | MENTION_EVERYONE` 权限，在与应用机器人用户的私信中额外包含 `USE_EXTERNAL_EMOJIS`

`****` : 该字段在除 PING 外的所有交互类型中可用

###### [交互类型](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type)

<table><thead><tr><th>名称</th><th>值</th></tr></thead><tbody><tr><td>PING</td><td>1</td></tr><tr><td>APPLICATION_COMMAND</td><td>2</td></tr><tr><td>MESSAGE_COMPONENT</td><td>3</td></tr><tr><td>APPLICATION_COMMAND_AUTOCOMPLETE</td><td>4</td></tr><tr><td>MODAL_SUBMIT</td><td>5</td></tr></tbody></table>

###### [交互上下文类型](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-context-types)

Discord 中可使用交互或触发交互的上下文。有关应用命令使用交互上下文的详细信息，请参阅[命令上下文文档](https://discord.com/developers/docs/interactions/application-commands#interaction-contexts)。

<table><thead><tr><th>名称</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>GUILD</td><td>0</td><td>交互可在服务器内使用</td></tr><tr><td>BOT_DM</td><td>1</td><td>交互可在与应用机器人用户的私信中使用</td></tr><tr><td>PRIVATE_CHANNEL</td><td>2</td><td>交互可在群组私信和除应用机器人用户外的私信中使用</td></tr></tbody></table>

`authorizing_integration_owners` 字段包含与交互相关的安装授权用户或服务器的详细信息。对于安装到用户的应用，可用于区分授权用户和触发交互的用户（如消息组件）。

仅当以下条件满足时才会存在键：

* 应用已获得与键对应的[安装上下文](https://discord.com/developers/docs/resources/application#application-object-application-integration-types)授权（`GUILD_INSTALL` 或 `USER_INSTALL`）
* 交互在键对应安装上下文的源[交互上下文](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-context-types)（`GUILD`、`BOT_DM` 或 `PRIVATE_CHANNEL`）中受支持
* 对于命令调用，命令必须在安装上下文中受支持（使用 [`integration_types`](https://discord.com/developers/docs/interactions/application-commands#contexts)）

`authorizing_integration_owners` 中的值取决于键——

* 如果键是 `GUILD_INSTALL`（`"0"`），值取决于交互来源：  
　* 如果交互从服务器触发，值将为服务器ID  
　* 如果交互从与应用机器人用户的私信触发，值将为 `"0"`  
* 如果键是 `USER_INSTALL`（`"1"`），值将为授权用户的ID

###### [交互数据](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-data)

虽然除 `PING` 外所有[交互类型](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type)的 `data` 字段都保证存在，但其结构会有所不同。以下表格详细说明了每种交互类型的内部 `data` 负载。

<table><thead><tr><th>交互类型</th><th>交互数据</th></tr></thead><tbody><tr><td>PING (<code>1</code>)</td><td>不适用</td></tr><tr><td>APPLICATION_COMMAND (<code>2</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-data-structure" data-discover="true">应用命令数据结构</a></td></tr><tr><td>MESSAGE_COMPONENT (<code>3</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-message-component-data-structure" data-discover="true">消息组件数据结构</a></td></tr><tr><td>APPLICATION_COMMAND_AUTOCOMPLETE (<code>4</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-data-structure" data-discover="true">应用命令数据结构</a></td></tr><tr><td>MODAL_SUBMIT (<code>5</code>)</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-modal-submit-data-structure" data-discover="true">模态提交数据结构</a></td></tr></tbody></table>

###### [应用命令数据结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-data-structure)

在`APPLICATION_COMMAND`和`APPLICATION_COMMAND_AUTOCOMPLETE`交互中发送。

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>id</td><td>雪花ID</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true"><code>ID</code></a> 调用的命令ID</td></tr><tr><td>name</td><td>字符串</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true"><code>name</code></a> 调用的命令名称</td></tr><tr><td>type</td><td>整数</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true"><code>type</code></a> 调用的命令类型</td></tr><tr><td>resolved?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-resolved-data-structure" data-discover="true">解析数据</a></td><td>转换后的用户+角色+频道+附件</td></tr><tr><td>options?*</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-interaction-data-option-structure" data-discover="true">应用命令交互数据选项</a>数组</td><td>来自用户的参数+值</td></tr><tr><td>guild_id?</td><td>雪花ID</td><td>命令注册到的服务器ID</td></tr><tr><td>target_id?</td><td>雪花ID</td><td>由<a href="https://discord.com/developers/docs/interactions/application-commands#user-commands" data-discover="true">用户</a>或<a href="https://discord.com/developers/docs/interactions/application-commands#message-commands" data-discover="true">消息</a>命令目标的用户或消息ID</td></tr></tbody></table>

`*` : 在响应`APPLICATION_COMMAND_AUTOCOMPLETE`时[可能是部分的](https://discord.com/developers/docs/interactions/application-commands#autocomplete)

###### [消息组件数据结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-message-component-data-structure)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>custom_id</td><td>字符串</td><td>组件的<a href="https://discord.com/developers/docs/components/reference#anatomy-of-a-component-custom-id" data-discover="true"><code>custom_id</code></a></td></tr><tr><td>component_type</td><td>整数</td><td>组件的<a href="https://discord.com/developers/docs/components/reference#component-object-component-types" data-discover="true">类型</a></td></tr><tr><td>values?*</td><td><a href="https://discord.com/developers/docs/components/reference#string-select-select-option-structure" data-discover="true">选择选项值</a>数组</td><td>用户在<a href="https://discord.com/developers/docs/components/reference#string-select" data-discover="true">选择菜单</a>组件中选择的值</td></tr><tr><td>resolved?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-resolved-data-structure" data-discover="true">解析数据</a></td><td>从选定选项中解析出的实体</td></tr></tbody></table>

`*` : 对于选择菜单组件，此字段始终存在

###### [模态提交数据结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-modal-submit-data-structure)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>custom_id</td><td>字符串</td><td>为模态提供的自定义ID</td></tr><tr><td>components</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-component-interaction-response-structures" data-discover="true">组件交互响应</a>数组</td><td>用户提交的值</td></tr></tbody></table>

###### [组件交互响应结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-component-interaction-response-structures)

<table><thead><tr><th>组件</th></tr></thead><tbody><tr><td><a href="https://discord.com/developers/docs/components/reference#string-select-string-select-interaction-response-structure" data-discover="true">字符串选择</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#text-input-text-input-interaction-response-structure" data-discover="true">文本输入</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#user-select-user-select-interaction-response-structure" data-discover="true">用户选择</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#role-select-role-select-interaction-response-structure" data-discover="true">角色选择</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#mentionable-select-mentionable-select-interaction-response-structure" data-discover="true">可提及选择</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#channel-select-channel-select-interaction-response-structure" data-discover="true">频道选择</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#text-display-text-display-interaction-response-structure" data-discover="true">文本显示</a></td></tr><tr><td><a href="https://discord.com/developers/docs/components/reference#label-label-interaction-response-structure" data-discover="true">标签</a></td></tr></tbody></table>

###### [解析数据结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-resolved-data-structure)

如果包含成员数据，则其相应用户的数据也将被包含。

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>users?</td><td>Snowflake到<a href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">用户</a>对象的映射</td><td>ID和用户对象</td></tr><tr><td>members?*</td><td>Snowflake到<a href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">部分成员</a>对象的映射</td><td>ID和部分成员对象</td></tr><tr><td>roles?</td><td>Snowflake到<a href="https://discord.com/developers/docs/topics/permissions#role-object" data-discover="true">角色</a>对象的映射</td><td>ID和角色对象</td></tr><tr><td>channels?**</td><td>Snowflake到<a href="https://discord.com/developers/docs/resources/channel#channel-object" data-discover="true">部分频道</a>对象的映射</td><td>ID和部分频道对象</td></tr><tr><td>messages?</td><td>Snowflake到<a href="https://discord.com/developers/docs/resources/message#message-object" data-discover="true">部分消息</a>对象的映射</td><td>ID和部分消息对象</td></tr><tr><td>attachments?</td><td>Snowflake到<a href="https://discord.com/developers/docs/resources/message#attachment-object" data-discover="true">附件</a>对象的映射</td><td>ID和附件对象</td></tr></tbody></table>

`*` : 部分`Member`对象缺少`user`、`deaf`和`mute`字段

`**` : 部分`Channel`对象仅包含`id`、`name`、`type`和`permissions`字段。线程还会包含`thread_metadata`和`parent_id`字段。

###### [应用命令交互数据选项结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-interaction-data-option-structure)

所有选项都有名称，选项可以是参数和输入值——此时将设置`value`——或者可以表示子命令或组——此时它将包含一个顶级键和另一个`options`数组。

`value`和`options`是互斥的。

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>name</td><td>字符串</td><td>参数的名称</td></tr><tr><td>type</td><td>整数</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-type" data-discover="true">应用命令选项类型</a>的值</td></tr><tr><td>value?</td><td>字符串、整数、双精度或布尔值</td><td>用户输入产生的选项值</td></tr><tr><td>options?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-application-command-interaction-data-option-structure" data-discover="true">应用命令交互数据选项</a>的数组</td><td>如果此选项是组或子命令，则存在</td></tr><tr><td>focused?</td><td>布尔值</td><td>如果此选项是自动补全当前聚焦的选项，则为<code>true</code></td></tr></tbody></table>

### [消息交互对象](https://discord.com/developers/docs/interactions/receiving-and-responding#message-interaction-object)

当消息是对没有现有消息的交互的响应时，将在[消息对象](https://discord.com/developers/docs/resources/message#message-object)上发送此对象。

###### [消息交互结构](https://discord.com/developers/docs/interactions/receiving-and-responding#message-interaction-object-message-interaction-structure)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>id</td><td>雪花ID</td><td>交互的ID</td></tr><tr><td>type</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type" data-discover="true">交互类型</a></td><td>交互的类型</td></tr><tr><td>name</td><td>字符串</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure" data-discover="true">应用命令</a>的名称，包括子命令和子命令组</td></tr><tr><td>user</td><td><a href="https://discord.com/developers/docs/resources/user#user-object" data-discover="true">用户对象</a></td><td>发起交互的用户</td></tr><tr><td>member?</td><td><a href="https://discord.com/developers/docs/resources/guild#guild-member-object" data-discover="true">部分成员</a>对象</td><td>在服务器中发起交互的成员</td></tr></tbody></table>

## [接收交互](https://discord.com/developers/docs/interactions/receiving-and-responding#receiving-an-interaction)

当用户与您的应用交互时，您的应用将收到一个[交互](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object)。您的应用可以通过以下两种方式之一接收交互：

*   通过[交互创建](https://discord.com/developers/docs/events/gateway-events#interaction-create)网关事件
*   通过传出webhook

这两种方法是互斥的；您只能通过其中一种方式接收交互。`INTERACTION_CREATE`[网关事件](https://discord.com/developers/docs/events/gateway-events#interaction-create)可以由连接的客户端处理，而下面详述的webhook方法不需要连接的客户端。

如果您想通过基于HTTP的传出webhook接收交互，您必须为您的应用配置一个交互端点URL。您可以在交互概述的[准备交互](https://discord.com/developers/docs/interactions/overview#preparing-for-interactions)部分阅读有关准备和添加交互端点URL到您的应用的信息。

### [交互元数据](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-metadata)

一个[交互](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object)包括元数据以帮助您的应用程序处理它，以及特定于交互类型的`data`。您可以在各自的页面上找到每种交互类型的示例：

*   [斜杠命令](https://discord.com/developers/docs/interactions/application-commands#slash-commands-example-interaction)
*   [用户命令](https://discord.com/developers/docs/interactions/application-commands#user-commands-example-interaction)
*   [消息命令](https://discord.com/developers/docs/interactions/application-commands#message-commands-example-interaction)
*   [消息组件](https://discord.com/developers/docs/components/using-message-components)
*   [模态组件](https://discord.com/developers/docs/components/using-modal-components)

所有字段的解释可以在我们的[数据模型](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object)中找到。

既然您已经从用户那里获取了数据，是时候回应他们了。

## [回应交互](https://discord.com/developers/docs/interactions/receiving-and-responding#responding-to-an-interaction)

交互——无论是接收还是回应——本质上都是webhook。因此，回应交互就像发送webhook请求一样！

交互响应具有与普通HTTP API请求相同的头部要求。更多信息请参见[此处](https://discord.com/developers/docs/reference#http-api)。

您可以通过多种方式回应交互：

### [交互响应对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object)

###### [交互响应结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-response-structure)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>type</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type" data-discover="true">交互回调类型</a></td><td>响应类型</td></tr><tr><td>data?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-data-structure" data-discover="true">交互回调数据</a></td><td>可选的响应消息</td></tr></tbody></table>

###### [交互回调类型](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type)

<table><thead><tr><th>名称</th><th>值</th><th>描述</th></tr></thead><tbody><tr><td>PONG</td><td>1</td><td>确认<code>Ping</code>请求</td></tr><tr><td>CHANNEL_MESSAGE_WITH_SOURCE</td><td>4</td><td>用消息响应交互</td></tr><tr><td>DEFERRED_CHANNEL_MESSAGE_WITH_SOURCE</td><td>5</td><td>确认交互并稍后编辑响应，用户会看到加载状态</td></tr><tr><td>DEFERRED_UPDATE_MESSAGE*</td><td>6</td><td>对于组件，确认交互并稍后编辑原始消息；用户不会看到加载状态</td></tr><tr><td>UPDATE_MESSAGE*</td><td>7</td><td>对于组件，编辑组件所附加的消息</td></tr><tr><td>APPLICATION_COMMAND_AUTOCOMPLETE_RESULT</td><td>8</td><td>用建议选项响应自动补全交互</td></tr><tr><td>MODAL**</td><td>9</td><td>用弹出模态框响应交互</td></tr><tr><td>PREMIUM_REQUIRED</td><td>10</td><td><a href="https://discord.com/developers/docs/change-log#premium-apps-new-premium-button-style-deep-linking-url-schemes" data-discover="true"><span>已弃用</span></a>；用升级按钮响应交互，仅适用于启用<a href="https://discord.com/developers/docs/monetization/overview" data-discover="true">货币化</a>的应用</td></tr><tr><td>LAUNCH_ACTIVITY</td><td>12</td><td>启动与应用关联的活动。仅适用于启用<a href="https://discord.com/developers/docs/activities/overview" data-discover="true">活动</a>的应用</td></tr></tbody></table>

`*` : 仅对[基于组件](https://discord.com/developers/docs/components/reference)的交互有效

`**` : 不适用于`MODAL_SUBMIT`和`PING`交互

###### [交互回调数据结构](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-data-structure)

###### [消息](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-messages)

并非所有消息字段目前都被支持

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>tts?</td><td>布尔值</td><td>响应是否为TTS</td></tr><tr><td>content?</td><td>字符串</td><td>消息内容</td></tr><tr><td>embeds?</td><td><a href="https://discord.com/developers/docs/resources/message#embed-object" data-discover="true">嵌入</a>数组</td><td>最多支持10个嵌入</td></tr><tr><td>allowed_mentions?</td><td><a href="https://discord.com/developers/docs/resources/message#allowed-mentions-object" data-discover="true">允许提及</a></td><td><a href="https://discord.com/developers/docs/resources/message#allowed-mentions-object" data-discover="true">允许提及</a>对象</td></tr><tr><td>flags? *</td><td>整数</td><td>作为<a href="https://en.wikipedia.org/wiki/Bit_field" rel="noreferrer noopener" target="_blank" role="button" tabindex="0">位域</a>组合的<a href="https://discord.com/developers/docs/resources/message#message-object-message-flags" data-discover="true">消息标志</a>（只能设置<code>SUPPRESS_EMBEDS</code>、<code>EPHEMERAL</code>、<code>IS_COMPONENTS_V2</code>、<code>IS_VOICE_MESSAGE</code>和<code>SUPPRESS_NOTIFICATIONS</code>）</td></tr><tr><td>components?</td><td><a href="https://discord.com/developers/docs/components/reference#component-object" data-discover="true">组件</a>数组</td><td>消息组件</td></tr><tr><td>attachments? **</td><td>部分<a href="https://discord.com/developers/docs/resources/message#attachment-object" data-discover="true">附件</a>对象数组</td><td>包含文件名和描述的附件对象</td></tr><tr><td>poll?</td><td><a href="https://discord.com/developers/docs/resources/poll#poll-create-request-object" data-discover="true">投票</a>请求对象</td><td>投票详情</td></tr></tbody></table>

`*` : 如果您使用[类型](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type) `DEFERRED_CHANNEL_MESSAGE_WITH_SOURCE` 创建回调，唯一有效的[消息标志](https://discord.com/developers/docs/resources/message#message-object-message-flags)是 `EPHEMERAL`。如果您想创建基于组件的消息并使用 `IS_COMPONENTS_V2`，必须通过[后续](https://discord.com/developers/docs/interactions/receiving-and-responding#followup-messages)消息实现，而不是本消息。

`**` : 详情请参阅[文件上传](https://discord.com/developers/docs/reference#uploading-files)。

###### [自动完成](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-autocomplete)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>choices</td><td><a href="https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-choice-structure" data-discover="true">选项</a>数组</td><td>自动完成选项（最多25个选项）</td></tr></tbody></table>

###### [模态框](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-modal)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>custom_id</td><td>字符串</td><td>模态框的开发人员定义标识符，最多100个字符</td></tr><tr><td>title</td><td>字符串</td><td>弹出模态框的标题，最多45个字符</td></tr><tr><td>components</td><td><a href="https://discord.com/developers/docs/components/reference#component-object" data-discover="true">组件</a>数组</td><td>构成模态框的1到5个（包含）组件</td></tr></tbody></table>

如果您的应用程序返回用户数据，应使用[`allowed_mentions`](https://discord.com/developers/docs/resources/message#allowed-mentions-object)来过滤内容中实际会触发通知的提及。

## [交互回调](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback)

当响应接收到的交互时，您可以向`/interactions/<interaction_id>/<interaction_token>/callback`发起`POST`请求。`interaction_id`是接收到的有效载荷中该特定交互的唯一ID。`interaction_token`是接收到的有效载荷中该交互的唯一令牌。

如果您通过网关接收交互，必须通过HTTP进行响应。对交互的响应不会作为命令通过网关发送。

如果您针对通过HTTP接收的交互发送此请求，请以202状态码且无正文响应对原始HTTP请求。

```
导入请求库

网址 = "https://discord.com/api/v10/interactions/<交互ID>/<交互令牌>/callback"

数据 = {
　　　　"类型": 4,
　　　　"数据": {
　　　　　　　　"内容": "恭喜发送命令！"
　　　　}
}
响应 = requests.post(网址, json=数据)
```

交互`令牌`有效期为15分钟，可用于发送后续消息，但必须在收到事件后3秒内发送初始响应。如果超过3秒期限，令牌将失效。

内联HTTP响应行为

###### [交互回调响应对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-response-object)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>交互</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-object" data-discover="true">交互回调对象</a></td><td>与交互响应关联的交互对象</td></tr><tr><td>资源?</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-resource-object" data-discover="true">交互资源对象</a></td><td>由交互响应创建的资源</td></tr></tbody></table>

###### [交互回调对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-object)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>ID</td><td>雪花ID</td><td>交互的ID</td></tr><tr><td>类型</td><td>整数</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-type" data-discover="true">交互类型</a></td></tr><tr><td>活动实例ID?</td><td>字符串</td><td>如果启动或加入了活动，则为活动的实例ID</td></tr><tr><td>响应消息ID?</td><td>雪花ID</td><td>由交互创建的消息ID</td></tr><tr><td>响应消息加载中?</td><td>布尔值</td><td>消息是否处于加载状态</td></tr><tr><td>响应消息临时?</td><td>布尔值</td><td>响应消息是否为临时消息</td></tr></tbody></table>

###### [交互回调资源对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-resource-object)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>type</td><td>integer</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type" data-discover="true">交互回调类型</a></td></tr><tr><td>activity_instance?*</td><td><a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-activity-instance-resource" data-discover="true">活动实例资源</a></td><td>表示由此交互启动的活动。</td></tr><tr><td>message?**</td><td><a href="https://discord.com/developers/docs/resources/message#message-object" data-discover="true">消息对象</a></td><td>由交互创建的消息。</td></tr></tbody></table>

`*` : 仅当类型为 `LAUNCH_ACTIVITY` 时存在。

`**` : 仅当类型为 `CHANNEL_MESSAGE_WITH_SOURCE` 或 `UPDATE_MESSAGE` 时存在。

###### [交互回调活动实例资源](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-activity-instance-resource)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>活动实例ID（如果已启动或加入活动）。</td></tr></tbody></table>

## [后续消息](https://discord.com/developers/docs/interactions/receiving-and-responding#followup-messages)

有时，您的机器人在响应交互后需要向用户发送后续消息。或者，您可能想要编辑原始响应。无论您是通过网关还是通过出站webhook接收交互，都可以使用以下端点编辑初始响应或发送后续消息：

*   [`PATCH /webhooks/<application_id>/<interaction_token>/messages/@original`](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-original-interaction-response) 编辑对交互的初始响应
*   [`DELETE /webhooks/<application_id>/<interaction_token>/messages/@original`](https://discord.com/developers/docs/interactions/receiving-and-responding#delete-original-interaction-response) 删除对交互的初始响应
*   [`POST /webhooks/<application_id>/<interaction_token>`](https://discord.com/developers/docs/interactions/receiving-and-responding#create-followup-message) 发送新的后续消息
*   [`PATCH /webhooks/<application_id>/<interaction_token>/messages/<message_id>`](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-followup-message) 编辑使用该`token`发送的消息

交互webhook与普通webhook共享相同的速率限制属性。

交互令牌有效期为15分钟，意味着您可以在该时间内响应交互。

### [端点](https://discord.com/developers/docs/interactions/receiving-and-responding#endpoints)

## [创建交互响应](https://discord.com/developers/docs/interactions/receiving-and-responding#create-interaction-response)

创建对交互的响应。请求体为[交互响应对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object)。除非`with_response`设置为`true`（此时返回`200`且响应体为[交互回调响应对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-response-object)），否则返回`204`。

此端点还支持类似于webhook端点的文件附件功能。有关上传文件和`multipart/form-data`请求的详细信息，请参阅[文件上传](https://discord.com/developers/docs/reference#uploading-files)。

###### [查询字符串参数](https://discord.com/developers/docs/interactions/receiving-and-responding#create-interaction-response-query-string-params)

<table><thead><tr><th>字段</th><th>类型</th><th>描述</th></tr></thead><tbody><tr><td>with_response?</td><td><a href="https://discord.com/developers/docs/reference#boolean-query-strings" data-discover="true">布尔值</a></td><td>是否包含<a aria-current="page" href="https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-callback-interaction-callback-response-object" data-discover="true">交互回调对象</a>作为响应</td></tr></tbody></table>

## [获取原始交互响应](https://discord.com/developers/docs/interactions/receiving-and-responding#get-original-interaction-response)

返回初始的交互响应。功能与[获取Webhook消息](https://discord.com/developers/docs/resources/webhook#get-webhook-message)相同。

## [编辑原始交互响应](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-original-interaction-response)

编辑初始的交互响应。功能与[编辑Webhook消息](https://discord.com/developers/docs/resources/webhook#edit-webhook-message)相同。

## [删除原始交互响应](https://discord.com/developers/docs/interactions/receiving-and-responding#delete-original-interaction-response)

删除初始的交互响应。成功时返回`204 No Content`。

## [创建后续消息](https://discord.com/developers/docs/interactions/receiving-and-responding#create-followup-message)

如果交互是由用户安装的应用发起且未在服务器中安装（即[授权集成所有者对象](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-authorizing-integration-owners-object)仅包含`USER_INSTALL`），则每个交互的应用限制为5条后续消息。

为交互创建后续消息。功能与[执行Webhook](https://discord.com/developers/docs/resources/webhook#execute-webhook)相同，但`wait`始终为true。使用此端点进行交互后续消息时，不支持`thread_id`、`avatar_url`和`username`参数。您可以使用`EPHEMERAL`[消息标志](https://discord.com/developers/docs/resources/message#message-object-message-flags)`1 << 6`（64）发送仅用户可见的消息。您也可以使用`IS_COMPONENTS_V2`[消息标志](https://discord.com/developers/docs/resources/message#message-object-message-flags)`1 << 15`（32768）发送基于[组件](https://discord.com/developers/docs/components/reference)的消息。

在响应交互后立即使用`DEFERRED_CHANNEL_MESSAGE_WITH_SOURCE`时，此端点将作为[编辑原始交互响应](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-original-interaction-response)以实现向后兼容性。在这种情况下，不会创建新消息，而是编辑加载消息。临时标志将被忽略，初始延迟响应中提供的值将被保留，因为现有消息的临时状态无法更改。此行为已弃用，您应在此情况下使用编辑原始交互响应端点。

## [获取后续消息](https://discord.com/developers/docs/interactions/receiving-and-responding#get-followup-message)

返回交互的后续消息。功能与[获取Webhook消息](https://discord.com/developers/docs/resources/webhook#get-webhook-message)相同。

## [编辑后续消息](https://discord.com/developers/docs/interactions/receiving-and-responding#edit-followup-message)

编辑交互的后续消息。功能与[编辑Webhook消息](https://discord.com/developers/docs/resources/webhook#edit-webhook-message)相同。

## [删除后续消息](https://discord.com/developers/docs/interactions/receiving-and-responding#delete-followup-message)

删除交互的后续消息。成功时返回`204 No Content`。
