--

*NOTE: These pages are aimed to be part of the role based guidance at the top level of this documentation, specifically aimed at professionals trying to move towards a particular outcome. They will refer and act as pointers to our official product documentation. The official product documentation will go into much more feature detail than the specific tutorial where they are referenced.

--

# What do you mean by 'Customizing Generative Answers' in Microsoft Copilot Studio?
The Generative Answers feature within Microsoft Copilot Studio works in the most simplest implementation by entering a public facing website into the configuration. The website would be used as a datasource to potentially answer questions without makers having to author any specific conversations. Other datasources can be used including authenticated and 3rd Party.

The behaviour from this feature can be customized. To customize the Generative Answer feature, this refers to making changes to the 'Conversations Booster' system topic within Copilot Studio using the built in Authoring Canvas within the studio. Modifying system topics should not be done without having a good understanding of the studio and always ensure you make a backup of the YAML before making any changes, so you can revert back to the original if needed.

Customizing this system topic means adding your own specific logic either before, or after the system behaviour which where the out of the box feature set is encapsulated within it (the 'Generative Answers' node). This means you can manipulate the input, or the output to suit your business needs. 

## What problem does it solve?
A large reason to modify the behaviour of Generative Answers is where organizations could be required to check for specific phrases or words, and then perform custom behaviour in the event of those phrases or words appearing or not appearing. This allows organizations to setup their own filtering and behaviour on high priority items for many reasons, including security, brand image or customer experience. 

# How to use it
To get started with this feature become familar with the Generative AI node within the authored canvas. This node allows you to utilize Generative Answers functionality directly within a canvas for specific use. Information can be found here on the basics of the node: https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-boost-node#add-a-generative-answers-node

Navigate to System Topics and check you can see 'Conversational Boosting' system topic. If you cannot, you have not enabled this in the Generative AI section of Copilot Studio. Navigate there as shown below and ensure it is enabled (reading any notices)

![Image of Boosted Conversations being enabled in System Topics](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Customize-Generative-Answers-Enable.png?raw=true)

An important point to understand when customizing or using the node is the node automatically sends the message to the canvas, so you won't see a 'sends message' node afterwards. 

![Image of GenAI Node and Send Message highlighted](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Customize-Generative-Answers-Send-Message.png?raw=true)

Uncheck this to not send this message, but when you do, this means you would be responsible to send the message, meaning you'll need to add your own message node, and use the system variable that is produced as the output within that message node (also shown in the screenshot above, which can be renamed as it has done in the example above). 

In the example below, within the Conversational Booster system topic, you can see the send message node is now unchecked

![Image of GenAI Node in system topic unchecked](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Customize-Generative-Answers-Modify-Node.png?raw=true)

Keeping the empty check the same, the example below shows a new variable being created of boolean type, and a powerFX function checking if the answer returned from Generative Answers contains a specific word, and if so, to set the variable value to true.

The powerfx code is: If("Xbox" in Topic.Answer, true)

Then a condition node is created where if this variable is true, to redirect the conversation to the 'escalate' system topic, and if not, to display the message with the original 'Answer' variable from Generative Answers.

![Image of added custom nodes in system topic](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Customize-Generative-Answers-Nodes.png?raw=true)

## Start below

This is a copy of the YAML from the customized system topic above. This is configured on the public website 'https://www.microsoft.com'


      - kind: AdaptiveDialog
      beginDialog:kind: OnUnknownIntent
      id: main
      priority: -1
      actions:
    - kind: SearchAndSummarizeContent
      id: search-content
      userInput: =System.Activity.Text
      moderationLevel: High
      tone: Friendly
      autoSend: false
      variable: Topic.Answer
      additionalInstructions:
      publicDataSource:
        sites:
          - "https://www.microsoft.com"

      sharePointSearchDataSource: {}
      responseCaptureType: TextOnly

    - kind: ConditionGroup
      id: has-answer-conditions
      conditions:
        - id: has-answer
          condition: =!IsBlank(Topic.Answer)
          actions:
            - kind: SetVariable
              id: setVariable_2bUViE
              variable: Topic.ContainsValue
              value: =If("Xbox" in Topic.Answer, true)

            - kind: ConditionGroup
              id: conditionGroup_yoGaDB
              conditions:
                - id: conditionItem_GbbE48
                  condition: =Topic.ContainsValue = true
                  actions:
                    - kind: BeginDialog
                      id: nJBIio
                      dialog: crf24_copilotGuideSamples.topic.Escalate

              elseActions:
                - kind: SendActivity
                  id: sendActivity_COwOYj
                  activity: "{Topic.Answer}"

            - kind: EndDialog
              id: end-topic
              clearTopicQueue: true