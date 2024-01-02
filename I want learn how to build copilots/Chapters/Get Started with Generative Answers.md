--

*NOTE: These pages are aimed to be part of the role based guidance at the top level of this documentation, specifically aimed at professionals trying to move towards a particular outcome. They will refer and act as pointers to our official product documentation. The official product documentation will go into much more feature detail than the specific tutorial where they are referenced.

--

# How do I get started with the 'Generative Answers' feature in Microsoft Copilot Studio?
Generative Answers in Microsoft Copilot Studio is an implementation of the RAG pattern and it is built with Azure OpenAI Services. It supports a variety of datasources to help you complete the 'search' operation of RAG before it summarizes the data and outputs an answer to a question. (See the homepage for this section included some basicson RAG and link to some additional education.)

Getting started with Generative Answers in Microsoft Copilot Studio has never been easier. The fastest way to get started is to enter your organizations public facing website into the 'Generative AI' page within Microsoft Copilot Studio, save the page and straight away in the test panel within Copilot Studio, begin asking questions relating to the data on the website you entered, and you can start to have multi-turn conversations.

## What problem does it solve?
Generative Answers in Copilot Studio allows companies to ground a conversational experience for their customers in their existing data set. This makes a customers experience more relevant to the organization they are interacting with. 

Copilot Studio makes this super easy and simple to setup and configure. Microsoft Copilot Studio is SaaS and does not require any additional insfrastructure to utilize the Generative AI features. This feature aims to save vast amounts of time where it can support a a wide range of customzers questions depending on the data source, without having to author each and every single question.
 
# How it works
Generative Answers is an implementation of the RAG pattern using Azure OpenAI Services. This means you must configure the search element of RAG and provide the data your organization wants to use and reference as an input to the feature for it to them summarize it.

* Supported datasources are being updated as part of the feature expanding, and include public facing websites, sharepoint, 3rd Party APIs through the node and Azure OpenAI on your data (inc. Cognitive Search)
* It supports anonymous and on behalf of security (the user asking the question)
* Multi-turn conversation support
* Build in checks e.g. security
* Supports adding additional custom prompts at the node level

Generative Answers can be surfaced in two ways with Copilot Studio:

* Copilot Scope: Configured under the 'Generative AI' section of the sitemap 
* Topic level Scope: Configured using the 'Generative answers' node within 'Advanced' in the authoring canvas

When a user asks a copilot built using Microsoft Copilot Studio a question, the first type of questions checked are the manually authored topics. A manually authored topic is a topic that has been created using Trigger Phrases and utilizes the out of the box Natural Language Understanding (NLU) model. If no manually authored topics are matched with the intent found in the question asked by the user, then the system topic is activated 'Conversation Booster' which uses the datasources configured at Copilot level to try and answer the question by the user and return an answer. You can also modify other behaviour, such as content moderation thresholds.

Generative Answers can also have a topic level scope. When a manually authored topic is triggered using the trigger phrases and out of the box NLU, a maker can use the Generative Answers node within the Advanced submenu in the authoring canvas of the studio to configure datasources in a similar way to the Copilot Scope, and leverage the same functionality. This is particularly useful if you want to still utilize manually authored topics and leverage Generative AI features in the scope of one or more specific topic.

The behaviour of Generative Answers is based on the datasources and other configuration details. For example whilst public facing websites do not require authentication, when configuring for SharePoint, this does require authentication. Authentication needs to be configured as the application is expected to use the logged in AAD token and use that to determine what the user has asking to.

# How to use it
The Microsoft Learn Documentation provides a compehensive set of guides on getting started with this feature in Microsoft Copilot Studio. The paths below are a suggested starting point, and it is recommended you use the extensive documentation on the core feature.

* Basics: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-boost-conversations
* More information on Information Sources you can use with Generative Answers: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-boost-node
* Use the Generative Answers Node: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-boost-node
* Using Bing Custom Search: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-generative-answers-bing

Some additional considerations using Generative Answers:

* Your datasource is important - review the supported datasources which include public facing websites, SharePoint, 3P APIs and Azure OpenAI on your Data (including Cognitive Search)
* You need to consider other factors including security - here is a blog post around this topic and other areas useful in discovery: https://microsoftcopilotstudio.microsoft.com/en-us/blog/create-generative-ai-solutions-with-power-virtual-agents-and-azure-openai-services/
* Generative answers can be used at copilot level or in an authored topic within the studio in a 'node' 
* 3rd Party Datasources can be connected through the Generative AI node