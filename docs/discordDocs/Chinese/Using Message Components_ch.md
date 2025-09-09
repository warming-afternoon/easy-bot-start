[概述](https://discord.com/developers/docs/components/using-message-components#overview)
--------------------------------------------------------------------------------------------

消息组件是为消息添加交互性的强大方式。它们允许您为用户创建丰富的交互式体验，使用户更容易与您的内容互动。

### [先决条件](https://discord.com/developers/docs/components/using-message-components#prerequisites)

*   您必须拥有 Discord 账户并是 Discord 开发者门户的成员。
*   您必须在 Discord 开发者门户中创建一个 Discord 应用程序。
*   您必须拥有在使用组件的频道中发送消息的必要权限。

* * *

[发送带有组件的消息](https://discord.com/developers/docs/components/using-message-components#sending-a-message-with-a-component)
------------------------------------------------------------------------------------------------------------------------------------------------

要发送带有组件的消息，您需要在消息的 `flags` 字段中设置 `IS_COMPONENTS_V2` 标志 (`1<<15`)。这可以在使用[创建消息](https://discord.com/developers/docs/resources/message#create-message)、[执行 Webhook](https://discord.com/developers/docs/resources/webhook#execute-webhook) 或[响应交互](https://discord.com/developers/docs/interactions/receiving-and-responding#create-followup-message)时完成。

设置 `IS_COMPONENTS_V2` 消息标志不可逆转：一旦消息发送，编辑消息时无法从消息中移除该标志。

此标志表示消息包含组件，并禁用传统内容和嵌入。

所有内容必须作为组件发送，而不是使用标准消息格式。

```
{
　　"flags": 32768,
　　"components": [
　　　　{
　　　　　　"type": 10,
　　　　　　"content": "这是一个使用文本显示组件的消息"
　　　　}
　　]
}
```

[发送带有多个组件的消息](https://discord.com/developers/docs/components/using-message-components#sending-a-message-with-multiple-components)
----------------------------------------------------------------------------------------------------------------------------------------------------------------

要发送带有多个组件的消息，您可以在消息的 `components` 字段中包含多个组件对象。此字段允许您指定将包含在消息中的组件数组。

```
{
　　"flags": 32768,
　　"components": [
　　　　{
　　　　　　"type": 10,
　　　　　　"content": "这是一个文本显示组件。"
　　　　},
　　　　{
　　　　　　"type": 10,
　　　　　　"content": "这是另一个文本显示组件！"
　　　　}
　　]
}
```

[使用布局组件嵌套组件](https://discord.com/developers/docs/components/using-message-components#nesting-components-with-layout-components)
--------------------------------------------------------------------------------------------------------------------------------------------------------------

您还可以在布局组件内嵌套组件。这为您在向用户显示信息、图像和交互式组件方面提供了更大的灵活性。查看[组件列表](https://discord.com/developers/docs/components/reference#component-object-component-types)以获取可用的布局组件的完整列表。

例如，您可以创建一个包含多个按钮组件的操作行组件的消息。

```
{
　　"flags": 32768,
　　"components": [
　　　　{
　　　　　　"type": 10,
　　　　　　"content": "这是一个带有 v2 组件的消息"
　　　　},
　　　　{
　　　　　　"type": 1,
　　　　　　"components": [
　　　　　　　　{
　　　　　　　　　　"type": 2,
　　　　　　　　　　"style": 1,
　　　　　　　　　　"label": "点击我",
　　　　　　　　　　"custom_id": "click_me_1"
　　　　　　　　},
　　　　　　　　{
　　　　　　　　　　"type": 2,
　　　　　　　　　　"style": 2,
　　　　　　　　　　"label": "也点击我",
　　　　　　　　　　"custom_id": "click_me_2"
　　　　　　　　}
　　　　　　]
　　　　}
　　]
}
```

[将消息组件与交互结合使用](https://discord.com/developers/docs/components/using-message-components#using-message-components-with-interactions)
----------------------------------------------------------------------------------------------------------------------------------------------------------------

当用户与交互式消息组件交互时，您的应用程序将[收到交互事件](https://discord.com/developers/docs/interactions/overview)。此事件包含有关交互的信息，包括交互类型和所交互的组件。

查看[支持的组件类型列表](https://discord.com/developers/docs/components/reference#component-object-component-types)以获取交互式消息组件及其交互事件负载的列表。

您可以使用此信息来响应交互、更新消息或执行其他操作，例如根据用户输入显示模态框。

查看[交互文档](https://discord.com/developers/docs/interactions/overview)以获取有关处理交互和响应来自交互式组件的用户输入的更多信息。
