--

*NOTE: These pages are aimed to be part of the role based guidance at the top level of this documentation, specifically aimed at professionals trying to move towards a particular outcome. They will refer and act as pointers to our official product documentation. The official product documentation will go into much more feature detail than the specific tutorial where they are referenced.

--

# What do you mean by the 'Plugins' feature in Microsoft Copilot Studio?
Copilots built using Microsoft Copilot Studio have the ability to have multi-turn coversations back and forth with the user, whether that is using Generative AI or manually authored behaviours. What makers will want to be able to do is also perform actions alongside those conversations, whether that is front of house or behind the scenes outside of the conversation. 

Plugins within Microsoft Copilot Studio are a way to perform actions through automation and processes. Plugins can be utilized when designing conversational experiences to add business value and help the customer get specific data or provide updates.

Types of plugins that can be used with Microsoft Copilot Studio include:
* Power Automate Flows 
* Plugin Actions (used in Generative Actions)
* Custom Connectors (Dataverse Connectors)
* Conversational Plugins
* OpenAI Plugins
* AI Builder Prompts

---
**NOTE:**

This documentation a MUST read to understand the plugin architecture in Microsoft Copilot Studio: https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-plugins-architecture
---

In addition to the methods above, makers can use HTTP connector action and also wrap some plugins and other actions within an Event when designing your conversational experience in an authored topic based on your needs.

## What problem does it solve?
Different types of plugins solve different problems, however generally, they solve the problem of an organization having to perform operations manually, like respond to a customer, update a row in a database or read and respond to emails. Instead the interaction can happen within a real time experience with a conversational agent or copilot, and the operations can be managed by the copilot and any output or update given to the customer in real time, as part of a single conversation.

# How to use plugins
The plugin types will each have their own way of being used within the studio. Below is the direct links to their respective Microsoft Learn Documentation

* Different types of Plugins: https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-plugins-overview#
* Copilot Studio Plugin Architecture: https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-plugins-architecture
* Conversational Plugins: https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-plugins-overview#conversational-plugins
* Power Automate Flows: https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-use-flow
* AI Builder Prompts: https://learn.microsoft.com/en-us/microsoft-copilot-studio/copilot-ai-plugins
* Plugin Actions: https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-plugin-actions

## Get Start below

### Power Platform Connectors
You can use Power Platform Connectors directly in Copilot Studio's runtime. You may want to do this for a number of reasons, for example the connector and studio runtime has everything you need, and this reduces handing over and returning control back to and from additional services.

To get started, make sure you have created the base of your authored topic, and when you are ready to use a connector, click the + icon on the studio's canvas to open up the menu. Click 'Call an action' and in the window, select 'Connector (preview)'. This opens a selection of connectors available to be used within Copilot Studio. In the example above, the 'SendEmailV2' connector was used to send an email directly from copilot studio.

Once you have selected your connector, it will be added to your authoring canvas. From here you need to enter the required data in the fields which are the minimum that are needed to be able to run the selected connector. In the example above, 'To', 'Subject' 'Body' and 'From' was required. 

When using a connector in this way, a new connection is created in the Power Platform which can be accessed via the make.powerapps.com and going to 'Connections' They can be modified here as well. The connection will be created with your logged in user credentials by default. In the example of the outlook connector, as it was created with a specific credential, I can only send emails using those authorized credentials. Some connectors will have specific requirements or configuration depending what it does.

If the selected connector has an output, it will be created as a variable accessible in the studio to be used, if needed.

The example below is where a copilot user asks for more information about a product, Generative Answers is used to generate the infomation using a public facing website

![Image of example connector in Copilot Studio Step 1](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/dvconnector-plugin-example-step1.png?raw=true)

Then that information is used to in the body of the email to send to the user for review at a later time. This is especially useful to be able to take a real time conversation and provide some details for reference to a customer or user. 

![Image of example connector in Copilot Studio Step 2](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/dvconnector-plugin-example-step2.png?raw=true)

// The YAML code is provided for illustratory purposes only for this example topic (and also the example used in the 'Power Automate Flows' example below) is available in the YAML code files in this reposortory. This topic will not work straight away as your own connection needs to be created within your environment, and you will likely get errors if you attempt to paste in the YAML without a connection to the connector used in the sample has not yet been created.

### Power Automate Flows
Power Automate Flows are a great way to run an encapsulated piece of logic from an authored topic in copilot studio. Power Automate Flow is classified as an action and has a specific entry and exit logic that 'bookends' the flow itself. If a flow is going to be run from copilot studio, these specific copilot studio entry and exit actions must be used. The easiest way to create a flow you intend to use with Power Automate is to create it from copilot studio.

![Image of example Flow in Power Automate](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Power-Automate-Flow-Action-Example.png?raw=true)

To get started, make sure you have created the base of your authored topic, and when you are ready to create a flow, click the + icon on the studio's canvas to open up the menu. Click 'Call an Action' and then click 'create a flow'. This will open a new window in your browser that automatically scaffolds the two required components on entry and exit of the flow. This is important because they behave as the 'hook' to be called from copilot studio and send data along with it. It additionally provides the exit call back to copilot studio, also sending any data back to the conversation with your user that can be used in conversations.

![Image of Power Automate interaction with Copilot Studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Power-Automate-Flow-Diagram.png?raw=true)

The sample flow used in this example with Power Automate is very simple. It has two required fields which must be entered within the copilot studio when configured. These are the email address and the message content we intend to email to the recipient. Then the Send Email connector is used and the required data is entered, some of which has come from the conversation input from copilot studio. No data is sent back to the studio, but the final connector must stay in place because it is provides the vehicle to go back to the copilot studio runtime when this flow is finished.

![Image of Power Automate interaction with Copilot Studio Step 1](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Power-Automate-Flow-Action-Example.png?raw=true)

![Image of Power Automate interaction with Copilot Studio Step 2](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/connector-plugin-example-step2.png?raw=true)

// The YAML code is provided for illustratory purposes only for this example topic (and also the example used in the 'Power Automate Flows' example below) is available in the YAML code files in this reposortory. This topic will not work straight away as your own connection needs to be created within your environment, and you will likely get errors if you attempt to paste in the YAML without a connection to the connector used in the sample has not yet been created.

### Plugin Actions (Coming soon)

### Conversational Plugins (Coming Soon)

### OpenAI Plugins (Coming Soon)

### AI Builder Prompts (Coming Soon)