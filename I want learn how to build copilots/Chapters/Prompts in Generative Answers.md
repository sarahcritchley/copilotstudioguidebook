--

*NOTE: These pages are aimed to be part of the role based guidance at the top level of this documentation, specifically aimed at professionals trying to move towards a particular outcome. They will refer and act as pointers to our official product documentation. The official product documentation will go into much more feature detail than the specific tutorial where they are referenced.

--

# What are Custom Prompt using Generative Answers in Microsoft Copilot Studio
Generative Answers can be used as a specific node (a node is a canvas block) within a topic that has been authored using the studio canvas. Using this node, you can use a range of datasources from public websites, sharepoint and even third party data that is formatted and passed into the node as the datasource.

An important feature about this node is you can use your own additional prompts via the 'Custom Instructions' section available in the node properties on the canvas.

## What problem does it solve?
Generative Answers is a first party feature in Copilot Studio that utilizes Azure OpenAI Services, and additionally has custom logic within the feature such as content moderation. It takes the users question as well as some of the conversation history for context as input to deterine an answer against configured datasources.  By adding a custom prompt directly in the copilot studio UI it allows specific instructions to be added by a maker, such as 'format the response in a list of bullet points' or 'provide an answer within 100 words' to improve the customer or users end experience.

# How to use it
Within an authored topic that is already setup with trigger phrases, click on the + icon to add a new node, click 'Advanced' and then click 'Generative Answers'

On the node properties, you will see an additional area called 'Custom instructions (preview)'. Add your custom prompt in this box and ensure you save the topic.

![Image of Generative Answers custom prompt](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/custom-prompt-image.png?raw=true)

## Start below
This is a snippet of YAML for the Generative Answer node with additionalInstructions being used in the example above:

            - kind: SearchAndSummarizeContent
              id: searchAndSummarizeContent_ld7SkO
              userInput: =System.LastMessage.Text
              moderationLevel: Medium
              autoSend: false
              variable: Topic.LaptopGenAnswer
              additionalInstructions: Provide some information on the types of laptop that Microsoft offers and standout features. Summarize the response in a bullet pointed list.
              publicDataSource:
                kind: PublicSiteSearchDataSource
                sites:
                  - microsoft.com