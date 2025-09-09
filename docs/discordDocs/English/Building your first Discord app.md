---
url: https://discord.com/developers/docs/quick-start/getting-started
time: 2025-09-10P22:11:58
tags: 
---
[Discord apps](https://discord.com/developers/docs/quick-start/overview-of-apps) let you customize and extend Discord using a collection of APIs and interactive features. This guide will walk you through building your first Discord app using JavaScript and by the end you'll have an app that uses slash commands, sends messages, and responds to component interactions.

If you're interested in building a game or social experience in an iframe, you can follow the tutorial for [building an Activity](https://discord.com/developers/docs/activities/building-an-activity)

We'll be building a Discord app that lets users play rock-paper-scissors (with 7 choices instead of 3). This guide is beginner-focused, but it assumes a basic understanding of [JavaScript](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics).

Resources used in this guide

Overview of the tools and technologies we'll use

* * *

## Step 0: Project Setup[](https://discord.com/developers/docs/quick-start/getting-started#step-0-project-setup)

Before we get started, you'll need to set up your local environment and get the project code from the [sample app repository](https://github.com/discord/discord-example-app).

We'll be developing our app locally with a little help from [ngrok](https://ngrok.com/), but you can use your preferred development environment.

If you don't have [NodeJS](https://nodejs.org/en/download/) installed, install that first.

After NodeJS is installed, open your command line and clone the project code:

```
git clone https://github.com/discord/discord-example-app.git
```

Then navigate to the directory and install the project's dependencies:

```
# navigate to directory
cd discord-example-app
 # install dependencies
npm install
```

Overview of the project structure for the sample app used in this tutorial

With that out of the way, open your new project in the code editor of your choice, and we'll move ahead to setting up your Discord app.

## Step 1: Creating an app[](https://discord.com/developers/docs/quick-start/getting-started#step-1-creating-an-app)

First, you'll need to create an app in the developer portal if you don't have one already:

[Create App](https://discord.com/developers/applications?new_application=true)

Enter a name for your app, then press Create.

After you create your app, you'll land on the General Information page of the app's settings where you can update basic information about your app like its description and icon. You'll also see an Application ID and Interactions Endpoint URL, which we'll use a bit later in the guide.

### Fetching your credentials[](https://discord.com/developers/docs/quick-start/getting-started#fetching-your-credentials)

We'll need to set up and fetch a few sensitive values for your app, like its token and ID.

Your token is used to authorize API requests and carry your app's permissions, so they are highly sensitive. Make sure to never share your token or check it into any kind of version control.

Back in your project folder, rename the `.env.sample` file to `.env`. This is where we'll store all of your app's credentials.

We'll need three values from your app's settings for your `.env` file:

*   On the General Information page, copy the value for Application ID. In `.env`, replace `<YOUR_APP_ID>` with the ID you copied.
*   Back on the General Information page, copy the value for Public Key, which is used to ensure HTTP requests are coming from Discord. In `.env`, replace `<YOUR_PUBLIC_KEY>` with the value you copied.
*   On the Bot page under Token, click "Reset Token" to generate a new bot token. In `.env`, replace `<YOUR_BOT_TOKEN>` with your new token.

You won't be able to view your token again unless you regenerate it, so make sure to keep it somewhere safe (like in a password manager).

Now that you have the credentials you need, lets configure your bot user and installation settings.

### Configuring your bot[](https://discord.com/developers/docs/quick-start/getting-started#configuring-your-bot)

Newly-created apps have a bot user enabled by default. Bot users allow your app to appear and behave similarly to other server members when it's [installed to a server](https://discord.com/developers/docs/quick-start/overview-of-apps#where-are-apps-installed).

On the left hand sidebar in your app's settings, there's a Bot page (where we fetched the token from). On this page, you can also configure settings like its [privileged intents](https://discord.com/developers/docs/events/gateway#privileged-intents) or whether it can be installed by other users.

Introduction to standard and privileged intents

For now, we don't need to configure anything additional here, but you may need to in the future depending on your app's use case. Let's go ahead and get our app ready for installation.

### Choosing installation contexts[](https://discord.com/developers/docs/quick-start/getting-started#choosing-installation-contexts)

Now we'll select where your app can be installed in Discord, which is determined by the [installation contexts](https://discord.com/developers/docs/resources/application#installation-context) that your app supports.

What are installation contexts?

Overview of where apps can be installed

Click on Installation in the left sidebar, then under Installation Contexts make sure both "User Install" and "Guild Install" are selected.

Some apps may only want to support one installation context—for example, a moderation app may only support a server context. However, by default, we recommend supporting both installation contexts. For detailed information about supporting user-installed apps, you can read the [user-installable app tutorial](https://discord.com/developers/docs/tutorials/developing-a-user-installable-app).

### Setting up an install link[](https://discord.com/developers/docs/quick-start/getting-started#setting-up-an-install-link)

[Install links](https://discord.com/developers/docs/resources/application#install-links) provide an easy way for users to install your app in Discord. We'll set up the default [Discord Provided Link](https://discord.com/developers/docs/resources/application#discord-provided-link), but you can read more about the different type of install links in the [Application documentation](https://discord.com/developers/docs/resources/application#types-of-install-links).

On the Installation page, go to the Install Link section and select "Discord Provided Link" if it's not already selected.

When Discorded Provided Link is selected, a new Default Install Settings section will appear, which we'll configure next.

### Adding scopes and bot permissions[](https://discord.com/developers/docs/quick-start/getting-started#adding-scopes-and-bot-permissions)

Apps need approval from installing users to perform actions in Discord (like creating a slash command or fetching a list of server members). Let's add scopes and permissions before installing the app.

What are scopes and permissions?

Introduction to scopes and bot permissions

On the Installation page in the Default Install Settings section:

*   For User Install, add the `applications.commands` scope
*   For Guild Install, add the `applications.commands` scope and `bot` scope. When you select `bot`, a new Permissions menu will appear to select the bot user's permissions. Select any permissions that you may want for your app—for now, I'll just select `Send Messages`.

![](https://discord.com/assets/4b14d5df50fb934c24a55895b6e67341.webp)

See a list of all [OAuth2 scopes](https://discord.com/developers/docs/topics/oauth2#shared-resources-oauth2-scopes), or read more on [permissions](https://discord.com/developers/docs/topics/permissions) in the documentation.

### Installing your app[](https://discord.com/developers/docs/quick-start/getting-started#installing-your-app)

When developing apps, you should build and test on your user account (for user-installable apps) and in a server that isn't actively used by others (for server-installable apps). If you don't have your own server already, you can [create one for free](https://support.discord.com/hc/en-us/articles/204849977-How-do-I-create-a-server-).

Once you add scopes, copy the URL from the Install Link section from before.

Since our app is supporting both installation contexts, we'll install your new app to both a test server and your user account so that we can test in both [installation contexts](https://discord.com/developers/docs/resources/application#installation-context).

###### Install to server[](https://discord.com/developers/docs/quick-start/getting-started#installing-your-app-install-to-server)

To install your app to your test server, copy the default Install Link for your app from the Installation page. Paste the link in your browser and hit enter, then select "Add to server" in the installation prompt.

Select your test server, and follow the installation prompt. Once your app is added to your test server, you should see it appear in the member list.

###### Install to user account[](https://discord.com/developers/docs/quick-start/getting-started#installing-your-app-install-to-user-account)

Next, install your app to your user account. Paste the same Install Link in your browser and hit enter. This time, select "Add to my apps" in the installation prompt.

Follow the installation prompt to install your app to your user account. Once it's installed you can open a DM with it.

* * *

## Step 2: Running your app[](https://discord.com/developers/docs/quick-start/getting-started#step-2-running-your-app)

With your app configured and installed to your test server and account, let's take a look at the code.

To make development a bit simpler, the app uses [discord-interactions](https://github.com/discord/discord-interactions-js), which provides types and helper functions. If you prefer to use other languages or libraries, check out the [Community Resources](https://discord.com/developers/docs/developer-tools/community-resources) documentation.

### Installing slash commands[](https://discord.com/developers/docs/quick-start/getting-started#installing-slash-commands)

To install slash commands, the app is using [`node-fetch`](https://github.com/node-fetch/node-fetch). You can see the implementation for the installation in `utils.js` within the `DiscordRequest()` function.

The project contains a `register` script you can use to install the commands in `ALL_COMMANDS`, which is defined at the bottom of `commands.js`. It installs the commands as global commands by calling the HTTP API's [`PUT /applications/<APP_ID>/commands`](https://discord.com/developers/docs/interactions/application-commands#bulk-overwrite-global-application-commands) endpoint.

If you want to customize your commands or add additional ones, you can reference the command structure in the [commands documentation](https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-structure).

In your terminal within the project folder, run the following command:

```
├── examples    -> short, feature-specific sample apps
│   ├── app.js  -> finished app.js code
│   ├── button.js
│   ├── command.js
│   ├── modal.js
│   ├── selectMenu.js
├── .env        -> your credentials and IDs
├── app.js      -> main entrypoint for app
├── commands.js -> slash command payloads + helpers
├── game.js     -> logic specific to Rock, Paper, Scissors
├── utils.js    -> utility functions and constants
├── package.json
├── README.md
└── .gitignore
```

If you navigate back to your server, you should see the slash commands appear. But if you try to run them, nothing will happen since your app isn't receiving or handling any requests from Discord.

Overview of Discord's HTTP and Gateway APIs

* * *

## Step 3: Handling interactivity[](https://discord.com/developers/docs/quick-start/getting-started#step-3-handling-interactivity)

To enable your app to receive slash command and other interactions requests, Discord needs a public URL to send them. This URL can be configured in your app's settings as Interaction Endpoint URL.

### Set up a public endpoint[](https://discord.com/developers/docs/quick-start/getting-started#set-up-a-public-endpoint)

To set up a public endpoint, we'll start our app which runs an [Express](https://expressjs.com/) server, then use [ngrok](https://ngrok.com/) to expose our server publicly.

First, go to your project's folder and run the following to start your app:

```
npm run register
```

There should be output indicating your app is running on port `3000`. Behind the scenes, our app is ready to handle interactions from Discord, which includes verifying security request headers and responding to `PING` requests. We're skipping over a lot of the details in this tutorial, but details about preparing apps for interactions is in the [Interactions Overview](https://discord.com/developers/docs/interactions/overview#preparing-for-interactions) documentation.

By default, the server will listen to requests sent to port 3000, but if you want to change the port, you can specify a `PORT` variable in your `.env` file.

Next, we'll start our ngrok tunnel. If you don't have ngrok installed locally, you can install it by following the instructions on the [ngrok download page](https://ngrok.com/download).

After ngrok is installed, open a new terminal and create a public endpoint that will forward requests to your Express server:

```
npm run start
```

You should see your connection open with output similar to the following:

```
ngrok http 3000
```

We'll use Forwarding URL as the publicly-accessible URL where Discord will send interactions requests in the next step.

### Adding an interaction endpoint URL[](https://discord.com/developers/docs/quick-start/getting-started#adding-an-interaction-endpoint-url)

Go to your [app's settings](https://discord.com/developers/applications) and on the General Information page under Interaction Endpoint URL, paste your new ngrok forwarding URL and append `/interactions`.

![](https://discord.com/assets/c227708d810abb94da4e8668565c05c4.webp)

Click Save Changes and ensure your endpoint is successfully verified.

If you have troubles verifying your endpoint, make sure both ngrok and your app are running on the same port, and that you've copied the ngrok URL correctly

The verification is handled automatically by the sample app in two ways:

*   It uses the `PUBLIC_KEY` and [discord-interactions package](https://github.com/discord/discord-interactions-js#usage) with a wrapper function (imported from `utils.js`) that makes it conform to [Express's `verify` interface](http://expressjs.com/en/5x/api.html#express.json). This is run on every incoming request to your app.
*   It responds to incoming `PING` requests.

You can learn more about preparing your app to receive interactions in [the interactions documentation](https://discord.com/developers/docs/interactions/overview#preparing-for-interactions).

### Handling slash command requests[](https://discord.com/developers/docs/quick-start/getting-started#handling-slash-command-requests)

With the endpoint verified, navigate to your project's `app.js` file and find the code block that handles the `/test` command:

```
Tunnel Status                 online
Version                       2.0/2.0
Web Interface                 http://127.0.0.1:4040
Forwarding                    https://1234-someurl.ngrok.io -> localhost:3000

Connections                  ttl     opn     rt1     rt5     p50     p90
                              0       0       0.00    0.00    0.00    0.00
```

The code above is responding to the interaction with a message in the channel, DM, or Group DM it originated from. You can see all available response types, like responding with a modal, [in the documentation](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-response-object-interaction-callback-type).

Go to your server and make sure your app's `/test` slash command works. When you trigger it, your app should send a message that contains “hello world” followed by a random emoji.

In the following section, we'll add an additional command that uses slash command options, buttons, and select menus to build the rock-paper-scissors game.

* * *

## Step 4: Adding message components[](https://discord.com/developers/docs/quick-start/getting-started#step-4-adding-message-components)

The `/challenge` command will be how our rock-paper-scissors-style game is initiated. When the command is triggered, the app will send message components to the channel, which will guide the users to complete the game.

### Adding a command with options[](https://discord.com/developers/docs/quick-start/getting-started#adding-a-command-with-options)

The `/challenge` command, called `CHALLENGE_COMMAND` in `commands.js`, has an array of `options`. In our app, the options are objects representing different things that a user can select while playing rock-paper-scissors, generated using keys of `RPSChoices` in `game.js`.

You can read more about command options and their structure [in the documentation](https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-structure).

While this guide won't touch much on the `game.js` file, feel free to poke around and change commands or the options in the commands.

Handling the command interaction

Code for handling the challenge command and responding with a message containing a button

Handling button interactions

Code for handling button clicks and responding with an ephemeral message

Handling select menu interactions

Code for responding to select menu interactions and updating the game state

....and that's it 🎊 Go ahead and test your app and make sure everything works.

* * *

## Next steps[](https://discord.com/developers/docs/quick-start/getting-started#next-steps)

Congrats on building your first Discord app! 🤖

Hopefully you learned a bit about Discord apps, how to configure them, and how to make them interactive. From here, you can continue building out your app or explore what else is possible.