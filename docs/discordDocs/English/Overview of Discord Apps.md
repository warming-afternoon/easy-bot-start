---
url: https://discord.com/developers/docs/quick-start/overview-of-apps
time: 2025-09-10P22:06:16
tags: 
---
# [Overview of Discord Apps](https://discord.com/developers/docs/quick-start/overview-of-apps#overview-of-discord-apps) 

![](https://discord.com/assets/a2b0db3a19d4540cbbb46d99ce17b45e.webp) 

Discord apps customize , extend , and enhance Discord for millions of users. Whether you're a developer interested in building an Activity , customizing servers , or integrating a game , apps are the container to bring your idea to life.

On this page we'll answer the questions:

* [What can apps do ? ](https://discord.com/developers/docs/quick-start/overview-of-apps#what-can-apps-do) 
* [Where are apps installed ? ](https://discord.com/developers/docs/quick-start/overview-of-apps#where-are-apps-installed) 
* [What APIs can apps use ? ](https://discord.com/developers/docs/quick-start/overview-of-apps#what-apis-can-apps-use) 

* * *

## What can apps do ? 

[](https://discord.com/developers/docs/quick-start/overview-of-apps#what-can-apps-do) 

You will discover the full possibility of apps as you explore the documentation and start building , but for now let's take a glance at some features you can build and integrate as you're developing your app.

### Send and manage messages[](https://discord.com/developers/docs/quick-start/overview-of-apps#send-and-manage-messages) 

Messages are a core part of Discord , and that's true for apps too. Apps can send messages in a few ways—they can call the [Create Message endpoint](https://discord.com/developers/docs/resources/message#create-message) , create and execute [webhooks](https://discord.com/developers/docs/resources/webhook) , or respond with a message when responding to an [interaction](https://discord.com/developers/docs/interactions/overview) 

Apps can also manage messages if they have the proper permissions , which is covered more in the [Message documentation](https://discord.com/developers/docs/resources/message) 

### Interact with users[](https://discord.com/developers/docs/quick-start/overview-of-apps#interact-with-users) 

Apps can use [interactions](https://discord.com/developers/docs/interactions/overview) to create more engaging and intuitive experiences for users. When sending messages , apps can send interactive components like [buttons](https://discord.com/developers/docs/components/reference#button) and [select menus](https://discord.com/developers/docs/components/reference#string-select) in the `components` field. Apps can also open form-like modals or launch an Activity [in response to interactions](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-modal) 

### Build embedded games and experiences[](https://discord.com/developers/docs/quick-start/overview-of-apps#build-embedded-games-and-experiences) 

Using the [Embedded App SDK](https://discord.com/developers/docs/developer-tools/embedded-app-sdk) , apps can create [Activities](https://discord.com/developers/docs/activities/overview) which are cross-platform interactive games and social experiences in Discord. They run in iframes in Discord , where people who play games are already hanging out.

### Customize servers[](https://discord.com/developers/docs/quick-start/overview-of-apps#customize-servers) 

With the right API endpoints and proper [permissions](https://discord.com/developers/docs/topics/permissions) , apps can customize the experience of using and moderating servers by accessing and customizing all sorts of resources core to Discord—including [users](https://discord.com/developers/docs/resources/user) , [channels](https://discord.com/developers/docs/resources/channel) , and [AutoMod](https://discord.com/developers/docs/resources/auto-moderation) to name a few. Explore the Resources documentation category to learn about the different Discord resources and how apps can use them.

### Update user metadata and presence[](https://discord.com/developers/docs/quick-start/overview-of-apps#update-user-metadata-and-presence) 

Apps can update a Discord's user metadata with data from a party game or app in a few ways. Apps can also update a user's profile with actionable data from a game or app by integrating [Rich Presence](https://discord.com/developers/docs/rich-presence/overview) 

Apps can also use [role connection metadata](https://discord.com/developers/docs/resources/application-role-connection-metadata) to associate third-party metadata (like stats or account type) with Discord users , which server admins can use to set up roles based on. You can explore more in the [configuring metadata for linked roles](https://discord.com/developers/docs/tutorials/configuring-app-metadata-for-linked-roles) tutorial.

### Add premium features[](https://discord.com/developers/docs/quick-start/overview-of-apps#add-premium-features) 

[App subscriptions](https://discord.com/developers/docs/monetization/implementing-app-subscriptions) let apps charge users and/or servers for premium functionality on a recurring basis natively within Discord. You can read more about eligibility and adding monetization features to your app in the [Monetization](https://discord.com/developers/docs/monetization/overview) documentation.

### ...and more[](https://discord.com/developers/docs/quick-start/overview-of-apps#and-more) 

This developer documentation is full of nooks and crannies with all sorts of features to explore. Discover the possibilities by exploring more of the docs , or by [building your own app](https://discord.com/developers/applications) 

* * *

## Where are apps installed ? 

[](https://discord.com/developers/docs/quick-start/overview-of-apps#where-are-apps-installed) 

Discord apps can be installed in two different contexts:

1. Apps installed to a server (called a [guild](https://discord.com/developers/docs/resources/guild) throughout the API) by a user with the Manage Server ([`MANAGE_GUILD`](https://discord.com/developers/docs/topics/permissions#permissions-bitwise-permission-flags) ) permission. Apps installed to a server can only be used within that server and DMs with the app's bot user , and are visible to all server members.
2. Apps installed to a user account. Apps installed to a user are visible only to that user , across all of their servers , DMs , and Group DMs by default.

The installation contexts that an app supports can be limited by the developer when [setting up the app](https://discord.com/developers/docs/resources/application#setting-supported-installation-contexts) 

Details about installation contexts are in the [Application resource documentation](https://discord.com/developers/docs/resources/application#installation-context) 

* * *

## What APIs can apps use ? 

[](https://discord.com/developers/docs/quick-start/overview-of-apps#what-apis-can-apps-use) 

There are a handful of different APIs that you can pick and choose from based on your app's functionality and which Discord features you want to access. Below is a quick overview of the main APIs on the Discord developer platform , but you can read more details and information about API usage in the [API reference](https://discord.com/developers/docs/reference) 

### HTTP API[](https://discord.com/developers/docs/quick-start/overview-of-apps#http-api) 

The HTTP API is a REST API that lets you interact and modify core Discord resources like [channels](https://discord.com/developers/docs/resources/channel) , [servers (or guilds) ](https://discord.com/developers/docs/resources/guild) , [users](https://discord.com/developers/docs/resources/user) , and [messages](https://discord.com/developers/docs/resources/message#message-object) 

Use the HTTP API to:

* Retrieve information about a resource
* Create , update , or delete a resource

Read details about using the HTTP API in the [API reference](https://discord.com/developers/docs/reference#http-api) 

### Gateway API[](https://discord.com/developers/docs/quick-start/overview-of-apps#gateway-api) 

The Gateway API lets you receive event data over a WebSocket anytime an [event](https://discord.com/developers/docs/events/gateway-events) occurs in a server where your app is installed.

Use the Gateway API to:

* Receive events happening in Discord

Read details about using the Gateway API in the [API reference](https://discord.com/developers/docs/reference#gateway-websocket-api) 

* * *

## Start Building[](https://discord.com/developers/docs/quick-start/overview-of-apps#start-building) 

Well , would you look at the time? With the basics out of the way , it's time to start building your Discord app ! You can explore the rest of the documentation , go to your [Apps](https://discord.com/developers/applications) , or explore the beginner resources below.

Develop your First App

[Tutorial to develop your first Discord app with interactive components](https://discord.com/developers/docs/quick-start/getting-started) 



Build an Activity on Discord

[Tutorial to develop an Activity using the Embedded App SDK](https://discord.com/developers/docs/activities/building-an-activity) 



Explore Developer Tools

[Explore community-built library and tools to speed up and simplify development](https://discord.com/developers/docs/developer-tools/community-resources) 