# Introduction to the Copilot Studio Guidebook
---
**NOTE:**
This collection of information is designed to be a goal based starting point for professionals who want to learn how to use Microsoft Copilot Studio to build custom copilots. 

This place is for beginners based on a specific goal. This content will go through the basics by breaking down key concepts, terminology, and basic platform functionality. It will include links to the official documentation for Microsoft Copilot Studio and could also contain other relevant links. Currently, we intent to grow the knowledge here to include more advanced content and are open to suggestions where they fit into the current layout & structure.

*HOW TO USE THIS CONTENT*::: 

Start at this homepage your reading now and work from top to bottom, this will give you the essential information. 

Readers can click the built-in URLs within the text to go learn specific things, and then return and continue on from where they left in the homepage. 

There are three roles that you can select from based on what your looking to do:

* [I want to learn how to build copilots in copilot studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/README.md)
* [I want to demo copilot studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20to%20demo%20copilot%20studio/README.md)
* I am starting a copilot studio project (coming soon)

Then when you have reviewed the content on this homepage, click the folder most relevant to what you are trying to do e.g. complete a demo, learn how to build copilots, or start a project and move on to the homepage in the relevant folder.

To read the content in a more ad-hoc way, navigate to the 'Chapters' subfolder in each section and select a specific item. Some subfolders will still be blank as the information continues to be curated. 

This content will be updated on an ad-hoc basis.

---

## Introduction

If you are new to building applications that take natural language as the input, there will be some things are going to be unfamilar to you. Let's begin by going through some of the foundations.

* Conversational AI can refer to conversations that use AI
* Natural Language (human language) is what humans use to talk to eachother, and what your using right now to read this text
* Natural Language is common to most human beings in some way, despite us having differences such as language, sentence structure and so on. As a result, humans can use natural lanuage to interact with humans successfully.
* We each have our own way of communicating in natural language, for example, we can ask a question and have many different ways to ask the same question
* When we build conversational experiences, we are building conversations and use AI technology to help manage that variability of natural language.
* Somebody would have asked you to 'rephrase that' at some point in your life. What did you do? Say the same thing, but differently. This shows a small part of the variability of natural language.

*Ultimately*, when building conversational experiences within copilots, we try to correctly descipher the intent or intents from a target users question and 'react' or answer that question if it is appropriate to do so. Additionally, and where applicable, we can configure the copilot to perform an action or some sort of automation as part of that reaction. All whilst providing a positive experience for the user that makes sense based on what they are using the copilot for.

## What is Microsoft Copilot Studio 

* Microsoft Copilot Studio is where your organizations can build your their custom copilots, their way
* A copilot is a conversational experience that utilizes Generative AI features from Microsoft with the aim that it acts as a 'copilot' to a human being
* You do not need to have developer experience to use Microsoft Copilot Studio to build Copilot
* Microsoft Copilot Studio is SaaS based and does not require any additional infrastructure to be provisioned to run many of the features, including it's built in Generative AI features
* This is distinct and in most cases, in addition to standard Conversational AI experiences that utilize NLU and NLP technology 
* Microsoft Copilot Studio is pre-built with an out of the box NLU. More information can be found [here](https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-gpt-quickstart) on the NLU.
* Microsoft Copilot Studio is available in various ways within Microsoft Business Applications technology. For example, it is available on it's own as a message based licence or together with Copilot for Microsoft 365.
* With your Copilot workflow in the studio experience, makers can also utilize plugins that are AI plugins using AI Builder, Plugins for M365 or coming soon, even utilize OpenAI GPTs

### What you need to know 

* A basic understanding of the core principals of Generative AI should be considered essential when building copilots. You don't have to seek out formal education and simply reading around this topic, of which there are many free courses avaiable that take only a few hours will help provide the understanding of the tehnological fundamentals so you can get the best value out of the Copilot Studio platform. 
* This entire course on Github by Carlotta Castellucio and team is a fantastic beginners course to core Generative AI principals: [Beginners Course for Generative AI](https://github.com/microsoft/generative-ai-for-beginners/tree/main/01-introduction-to-genai)
* Copilot makers can use many of the pre-built features directly from Microsoft Copilot Studio and have a chatGPT like experience without having to connect themselves to a LLM or build their own RAG architecture.
* Microsoft Copilot Studio has three main Generative AI features: Generative Answers, Generative Actions and for building in Copilot Studio, it's own Copilot
* Learn more about Generative Answers here: [Get started with Generative Answers](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Get%20Started%20with%20Generative%20Answers.md)
* Generative Answers utilize RAG by utilizing only the data you specifically want to use to ground questions. RAG stands for Retrieval Augmented Generation (RAG) and it is an approach to improve LLM results by grounding a prompt with a specific data set. 
* More information on RAG can be found in this section of the Generative AI for Beginners Course here: [Learn more about RAG](https://github.com/microsoft/generative-ai-for-beginners/blob/main/02-exploring-and-comparing-different-llms/README.md)
* You can craft and design conversational experiences that perform actions in different ways, using plugins, flows and even Generative AI with the Generative Actions feature. Read more about that: [Perform Actions with Plugins in Copilot Studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Copilot%20Studio%20Plugins.md)
* It is important to create copilots responsibility and Microsoft provide tools and resources to ensure you are considering the impact of your copilot: [Responsible AI Toolbox](https://responsibleaitoolbox.ai/)
* You should know core Conversational AI principals such as Disambiguation, Fallback Basics, Single Turn and Multi-turn conversations. Check out the respective pages in these links: [Disambiguation](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Disambiguation%20Basics.md) | [Single and Multi Turn Conversations](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Single%20and%20Multi-Turn%20Conversations.md) | [Fallback Basics](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Fallback%20Basics.md)
* Microsoft Copilot Studio has the ability for makers to create their own dialog within the studio canvas, often referred to as 'Manually authored topics or conversations'. Even though these are manually authored, they are still dynamic to the users questions and responses, can contain multiple conditional branches and are triggered by the out of the box Natural Language Understanding Model (NLU), still using AI
* You might want to use a manually authored topic to ensure specific responses always occur in certain cases or topics
* Makers can also use the studio's canvas to modify some of the Generative AI behaviour. This is covered in more depth [Customize Generative Answers in Copilot Studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Customize%20Generative%20Answers.md)
* In many cases, organizations will want to use a combination of both manually authored topics and Generative AI features
* The unit of cost for Microsoft Copilot Studio standalone is messages: [Copilot Studio Pricing](https://www.microsoft.com/en-us/microsoft-copilot/microsoft-copilot-studio#Pricing) and [Copilot Studio Quotas](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-quotas) however if you are using the studio with other applications like Copilot for Microsoft 365 or Dynamics 365 Customer Service, licencing will be different. Check out the licencing based on the products your going to purchase.

### Practical things to GO DO in Copilot Studio

---
**NOTE:**
Go check out these official docs which provide a guided experience on key tasks to ensure you complete. Skipping these simple tasks will mean your learning journey is more difficult:

---

* Create a copilot: https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-first-bot?tabs=web

* Connect to a website or another datasource using Generative Answers: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-boost-conversations

* Author topics within the studio using Copilot: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-gpt-overview
    * or manually: https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-fundamentals?tabs=web

* Publish your bot: https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-fundamentals-publish-channels?tabs=preview

## Next Steps

Based on what your goals select the links below to continue your journey and expand your knowledge:

* [I want to learn how to build copilots in copilot studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/README.md)
* [I want to demo copilot studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20to%20demo%20copilot%20studio/README.md)
* I am starting a copilot studio project (coming soon)

## Resources
Here is a list of resources which will be updated available in the public domain that will help you on your journey.

* Copilot Studio Playbook - note this is formatted with our foundational product, Power Virtual Agents, and is relevant too for Microsoft Copilot Studio: [Access the playbook here](https://aka.ms/pvaplaybook) 

* Copilot Studio Implementation Guide for use in projects: [Access the implementation guide](https://aka.ms/copilotstudioimplementationguide) 

* Copilot Studio in a Day (CiaD) - Guided Microsoft Learn Student material accessed [here](https://learn.microsoft.com/en-us/training/paths/power-virtual-agents-workshop/)

### Microsoft Partner Specific Links 

* If you are a Microsoft Partner and want to grow your knowledge, check out the Microsoft Copilot Studio Partner Growth Plan [here](https://aka.ms/copilotstudio/partnergrowthplan)

* Check out the Dynamics and Power Platform Partner Hub for updated decks and information to help help drive conversations