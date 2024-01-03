# Demo creating authored topics in Microsoft Copilot Studio
This page covers a short walkthrough on setting up how to demo authored topic behaviour for Microsoft Copilot Studio for demonstration purposes.

## Create Manually Authored Topics
Microsoft Copilot Studio has the capabilities to combine Generative AI capabilities with more determined and dynamic authored conversational experiences that follow the same pattern.

This lets companies obtain the scale benefits of Generative AI features like Generative Answers, and at the same time for critical path topics where it should always follow a specific path or line of questioning, they have the authoring studio available to create those.

For clarity:

* A manually authored topic is a topic that uses trigger phrases, that has been created either by you, or by the built-in copilot, where it is saved as a 'Topic' in the topic list within Microsoft Copilot Studio. That topic is triggered by trigger phrases and uses the out of the box NLU or a custom CLU model.
* Generative Answers can be configured at Copilot Level that is capable of answering multi-turn questions and will only activate when there is no manually authored topics found to be matching the current intent from the user's question based on the configured NLU.

When creating a demo flow, is important to showcase the authoring studio and the extensive capabilities a maker has access to be able to created authored experiences. These features can easily be combined following a discussion of the out of the box Generative AI features, like Generative Answers.

You can demostrate authored topics in two ways, one by having a prebuilt topic already created and another by showing the authoring studio features live by using the built-in copilot to automatically create an authored topic.

The example below is a simple product information type scenario. Change the scenario to meet your needs.

1. To create an authored topic, open your copilot and click 'Topics and Plugins'

2. Click 'Add', 'Topic' then you will have two choices: 'From blank' or 'Create from description' Click 'Create from description'

3. Add in the following description into the description box and name your topic 'Product Information':

*When a customer asks about product information and product details of the type of items that are sold, ask the question what types of products are they interested in, and offer two options for the customer to select, laptop or game consoles*

4. This will create the trigger phrases and a few message and question nodes automatically for you to get started with.

5. Add a new condition by selecting + at the bottom of the branch in the authoring canvas and create two new branches based on the variable value being either 'Games Consoles' or 'Laptops'. You will need to select the '+' icon in the middle of the condition to add the second branch.

6. You can either add information about the topic or use a website such as microsoft.com to surface the information about Laptops for this example. Do this by adding a custom node via the menu 'Advanced', 'Generative answers' and then configuring the node with the website and custom prompt. 

7. Provide the output of the answer in a message

8. Add a follow up message if they would like to ask any other questions

Other suggestions on showcasing the authoring canvas can include:

* Adding adaptive cards
* Using Plugins such as Power Automate flows to retrieve external data [Learn more here](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Copilot%20Studio%20Plugins.md)
* Using Entities and Slot Filling
* Building a custom event topic

*More pages will be added in the future*

### Key Demo Highlights

* Manually authored topics are important to discuss as they offer a specific authored path for companies, that is the same every time, based on the trigger phrases set. 

* There are a number of features the authoring canvas has to be able to display information and create an interactive experience that is conversational and natural. 

* The authoring canvas allows any professional at any skill level to begin authoring conversational dialogs.

# Get Started Below

    kind: AdaptiveDialog
    beginDialog:
    kind: OnRecognizedIntent
    id: main
    intent:
    triggerQueries:
      - product information
      - tell me about the product
      - what can you tell me about this product
      - give me details about the product
      - product specs
      - features of the product
      - what is this product all about?
      - information on the product
      - product description

    - actions:
    - kind: Question
      id: Question_2SkQIw
      variable: Topic.ProductType
      prompt: Absolutely! What type of products are you interested in?
      entity:
        kind: EmbeddedEntity
        definition:
          kind: ClosedListEntity
          optionSetName: ProductTypeOptions
          items:
            - id: laptop
              displayName: Laptop

            - id: game_consoles
              displayName: Game Consoles

    - kind: ConditionGroup
      id: conditionGroup_17fyne
      conditions:
        - id: conditionItem_1ebSNJ
          condition: =Topic.ProductType = ProductTypeOptions.laptop
          actions:
            - kind: SendActivity
              id: sendActivity_dnie8i
              activity: Thanks for enquiring about the laptops we offer. 

            - kind: Question
              id: question_Vzl0Qm
              interruptionPolicy:
                allowInterruption: true

              variable: init:Topic.AdditionalDetail
              prompt: Is there any specific laptop you are interested in or would you perfer some general information?
              entity: StringPrebuiltEntity

            - kind: SearchAndSummarizeContent
              id: searchAndSummarizeContent_ih0xhi
              userInput: Product information on Laptops
              autoSend: false
              variable: Topic.GeneratedResponse
              additionalInstructions: Include information about Laptops Microsoft offers and also include anything about this information:{{Topic.AdditionalDetail}}
              publicDataSource:
                sites:
                  - microsoft.com

              sharePointSearchDataSource: {}
              customDataSource: {}

            - kind: SendActivity
              id: sendActivity_QCwkst
              activity: "{Topic.GeneratedResponse}"

        - id: conditionItem_DJdKVD
          condition: =Topic.ProductType = ProductTypeOptions.game_consoles

      elseActions:
        - kind: BeginDialog
          id: sYQvOm
          dialog: crf24_copilotGuideSamples.topic.Escalate

        - kind: CancelAllDialogs
          id: MFY4f0

    - kind: SendActivity
      id: sendActivity_HYyap9
      activity: Do you have any other questions?