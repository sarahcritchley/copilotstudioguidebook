# Demo Custom Prompts in Microsoft Copilot Studio
This page covers a short walkthrough on setting up Custom Prompts behaviour for Microsoft Copilot Studio for demonstration purposes.

## Configure Custom Prompts
Custom Prompts with Generative Answers is only available using the node within the authoring canvas (and not available at 'Copilot' level, only 'Topic' level)

1. To configure Custom Prompts, open a manually authored topic and where you want to use the Generative Answer node, click the + icon and select 'Advanced' and 'Generative answers'

2. In the input, select the variables and add the 'LastMessage.Text' variable to enter the last thing said in the Coilot

3. Configure your datasources, by selecting 'Edit' on the node, selecting Datasources on the right hand panel and adding your data. The sample below and in the screenshots uses the Microsoft website.

![Image of configuring datasources](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20to%20demo%20copilot%20studio/Images/configuredatasources.png?raw=true)

4. Click back on the right hand panel and you should see a text box called 'Custom Instructions' (preview)

5. Enter some custom instructions e.g. summarize the response in bullet points

6. Save your topic. 

Before you begin testing ensure you have completed the rest of your manually authored topic and have an place where the answer for the Generative Answers node you have added is displayed. (The sample below has the variable displayed in a message node)

### Key Demo Highlights
Custom Instructions allow makers to:

* Add to the managed behaviour of Generative Answers and customize the response
* Give more access and control to how the responses are displayed

# Get Started Below

    kind: AdaptiveDialog
    beginDialog:
    kind: OnRecognizedIntent
    id: main
    intent:
    triggerQueries:
      - Send product information
      - Let me know about a product
      - Send me some information around products
      - email me product data
      - product data

  actions:
    - kind: SendActivity
      id: sendActivity_8liLq1
      activity: Absolutely - first let me get some information about specific products your interested in

    - kind: Question
      id: question_Tafb64
      interruptionPolicy:
        allowInterruption: true

      variable: init:Topic.ProductSelection
      prompt: What products are you interested in?
      entity:
        kind: ClosedListEntityReference
        entityId: crf24_copilotGuideSamples.entity.Products
        selectedItems:
          - JtZSNl
          - mCgpM5
          - 3fVa8m

    - kind: ConditionGroup
      id: conditionGroup_fRcttc
      conditions:
        - id: conditionItem_1fNaQS
          condition: =Topic.ProductSelection = 'crf24_copilotGuideSamples.entity.Products'.mCgpM5
          actions:
            - kind: SendActivity
              id: sendActivity_NEucvH
              activity: Thank you for your selection. I can provide some initial information around the laptops we offer over chat now, and then email it over to you

            - kind: SearchAndSummarizeContent
              id: searchAndSummarizeContent_ld7SkO
              userInput: =System.LastMessage.Text
              moderationLevel: Medium
              autoSend: false
              variable: Topic.LaptopGenAnswer
              additionalInstructions: Provide some information on the types of laptop that Microsoft offers and standout features. Summarize the response in a bullet pointed list.
              publicDataSource:
                sites:
                  - microsoft.com

              sharePointSearchDataSource: {}
              customDataSource: {}

            - kind: SendActivity
              id: sendActivity_DfMbTk
              activity: "{Topic.LaptopGenAnswer}"

        - id: conditionItem_YFQO0x
          condition: =Topic.ProductSelection = 'crf24_copilotGuideSamples.entity.Products'.'3fVa8m'

    - kind: SendActivity
      id: sendActivity_wGuWwj
      activity: Do you have any other questions?