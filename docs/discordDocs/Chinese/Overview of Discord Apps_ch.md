# [Discord应用概览](https://discord.com/developers/docs/quick-start/overview-of-apps#overview-of-discord-apps) 

Discord应用为数百万用户定制、扩展和增强Discord体验。无论您是想要构建活动、自定义服务器还是集成游戏的开发者，应用都是将您的想法变为现实的容器。

本页将回答以下问题：

* [应用能做什么？](https://discord.com/developers/docs/quick-start/overview-of-apps#what-can-apps-do) 
* [应用安装在何处？](https://discord.com/developers/docs/quick-start/overview-of-apps#where-are-apps-installed) 
* [应用可以使用哪些API？](https://discord.com/developers/docs/quick-start/overview-of-apps#what-apis-can-apps-use) 

* * *

## [应用能做什么？ ](https://discord.com/developers/docs/quick-start/overview-of-apps#what-can-apps-do) 

当您探索文档并开始构建时，您会发现应用的全部可能性，但让我们先来看看在开发应用时可以构建和集成的一些功能。

### [发送和管理消息](https://discord.com/developers/docs/quick-start/overview-of-apps#send-and-manage-messages) 

消息是Discord的核心部分，对应用也是如此。应用可以通过几种方式发送消息——可以调用[创建消息端点](https://discord.com/developers/docs/resources/message#create-message)、创建和执行[webhooks](https://discord.com/developers/docs/resources/webhook)，或在响应[交互](https://discord.com/developers/docs/interactions/overview)时返回消息。 

如果应用具有适当权限，还可以管理消息，这在[消息文档](https://discord.com/developers/docs/resources/message)中有更详细的介绍。 

### [与用户互动](https://discord.com/developers/docs/quick-start/overview-of-apps#interact-with-users) 

应用可以使用[交互](https://discord.com/developers/docs/interactions/overview)为用户创造更具吸引力和直观的体验。发送消息时，应用可以在`components`字段中发送交互式组件，如[按钮](https://discord.com/developers/docs/components/reference#button)和[选择菜单](https://discord.com/developers/docs/components/reference#string-select)。应用还可以打开类似表单的模态窗口或启动活动[以响应交互](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-modal)。 

### [构建嵌入式游戏和体验](https://discord.com/developers/docs/quick-start/overview-of-apps#build-embedded-games-and-experiences) 

使用[嵌入式应用SDK](https://discord.com/developers/docs/developer-tools/embedded-app-sdk)，应用可以创建[活动](https://discord.com/developers/docs/activities/overview)，这些是在Discord中的跨平台互动游戏和社交体验。它们在Discord的iframe中运行，玩家们已经在那里聚集。

### [自定义服务器](https://discord.com/developers/docs/quick-start/overview-of-apps#customize-servers) 

通过正确的API端点和适当的[权限](https://discord.com/developers/docs/topics/permissions)，应用可以通过访问和自定义Discord核心的各种资源来定制使用和管理服务器的体验，包括[用户](https://discord.com/developers/docs/resources/user)、[频道](https://discord.com/developers/docs/resources/channel)和[自动审核](https://discord.com/developers/docs/resources/auto-moderation)等。探索资源文档类别，了解不同的Discord资源以及应用如何使用它们。

### [更新用户元数据和状态](https://discord.com/developers/docs/quick-start/overview-of-apps#update-user-metadata-and-presence) 

应用可以通过几种方式使用来自派对游戏或应用的数据来更新Discord用户的元数据。应用还可以通过集成[丰富状态](https://discord.com/developers/docs/rich-presence/overview)来使用来自游戏或应用的可操作数据更新用户的个人资料。 

应用还可以使用[角色连接元数据](https://discord.com/developers/docs/resources/application-role-connection-metadata)将第三方元数据（如统计数据或账户类型）与Discord用户关联，服务器管理员可以基于此设置角色。您可以在[为链接角色配置元数据](https://discord.com/developers/docs/tutorials/configuring-app-metadata-for-linked-roles)教程中了解更多信息。

### [添加高级功能](https://discord.com/developers/docs/quick-start/overview-of-apps#add-premium-features) 

[应用订阅](https://discord.com/developers/docs/monetization/implementing-app-subscriptions)允许应用直接在Discord内向用户和/或服务器定期收取高级功能费用。您可以在[变现](https://discord.com/developers/docs/monetization/overview)文档中阅读更多关于资格条件和为应用添加变现功能的信息。

### [...以及更多](https://discord.com/developers/docs/quick-start/overview-of-apps#and-more) 

这份开发者文档包含各种功能的细节，值得深入探索。通过浏览更多文档或[构建您自己的应用](https://discord.com/developers/applications)来发现更多可能性。 

* * *

## [应用安装在哪里？ ](https://discord.com/developers/docs/quick-start/overview-of-apps#where-are-apps-installed) 

Discord应用可以在两种不同的环境中安装：

1. 由具有管理服务器（[`MANAGE_GUILD`](https://discord.com/developers/docs/topics/permissions#permissions-bitwise-permission-flags)）权限的用户安装到服务器（在API中称为[公会 (guild)](https://discord.com/developers/docs/resources/guild)）。安装到服务器的应用只能在该服务器内以及与应用的机器人用户的私信中使用，并且对所有服务器成员可见。
2. 安装到用户账户的应用。默认情况下，安装到用户的应用仅对该用户在所有服务器、私信和群组私信中可见。

开发者可以在[设置应用](https://discord.com/developers/docs/resources/application#setting-supported-installation-contexts)时限制应用支持的安装环境。 

有关安装环境的详细信息，请参阅[应用资源文档](https://discord.com/developers/docs/resources/application#installation-context)。 

* * *

## [应用可以使用哪些API？ ](https://discord.com/developers/docs/quick-start/overview-of-apps#what-apis-can-apps-use) 

有多种不同的API可供您根据应用的功能和想要访问的Discord功能进行选择。以下是Discord开发者平台上主要API的简要概述，但您可以在[API参考](https://discord.com/developers/docs/reference)中阅读更多关于API使用的详细信息。 

### [HTTP API](https://discord.com/developers/docs/quick-start/overview-of-apps#http-api) 

HTTP API是一个REST API，允许您与核心Discord资源（如[频道](https://discord.com/developers/docs/resources/channel)、[服务器](https://discord.com/developers/docs/resources/guild)、[用户](https://discord.com/developers/docs/resources/user)和[消息](https://discord.com/developers/docs/resources/message#message-object)）进行交互和修改。 

使用HTTP API可以：

* 检索资源信息
* 创建、更新或删除资源

在[API参考](https://discord.com/developers/docs/reference#http-api)中阅读有关使用HTTP API的详细信息。 

### [网关API](https://discord.com/developers/docs/quick-start/overview-of-apps#gateway-api) 

网关API允许您通过WebSocket在安装应用的服务器中发生[事件](https://discord.com/developers/docs/events/gateway-events)时接收事件数据。

使用网关API可以：

* 接收Discord中发生的事件

在[API参考](https://discord.com/developers/docs/reference#gateway-websocket-api)中阅读有关使用网关API的详细信息。 

* * *

## [开始构建](https://discord.com/developers/docs/quick-start/overview-of-apps#start-building) 

好了，时间到了吗？掌握了基础知识后，是时候开始构建您的Discord应用了！您可以浏览其余文档，前往您的[应用](https://discord.com/developers/applications)，或探索以下初学者资源。

开发您的第一个应用

[使用交互式组件开发第一个Discord应用的教程](https://discord.com/developers/docs/quick-start/getting-started) 


在Discord上构建活动

[使用嵌入式应用SDK开发活动的教程](https://discord.com/developers/docs/activities/building-an-activity) 


探索开发者工具

[探索社区构建的库和工具，以加速和简化开发](https://discord.com/developers/docs/developer-tools/community-resources) 
