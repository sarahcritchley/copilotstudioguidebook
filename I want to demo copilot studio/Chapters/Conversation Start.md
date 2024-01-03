# Demo Conversation Start in Microsoft Copilot Studio
This page covers a short walkthrough on setting up Conversation Start behaviour for Microsoft Copilot Studio for demonstration purposes.

## Configure Conversation Start
Conversation Start is the first message sent by the Copilot to the user. This message by default is set to run automatically and it is run from the system topic 'Conversation Start' system topic.

![Image of Conversation Start behaviour in Copilot Studio](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20to%20demo%20copilot%20studio/Images/Conversation%20Start%20.png?raw=true)

The default behaviour is a message node with text.

This system topic can be customized and some suggestions on showcasing the ability to configure this includes

* Updating the message node your own text in the message node
* Include multiple message varations in the message node to add degrees of variability and more natural
* You could retrieve data from a connector for example and display some relevant information based on the scope of the copilot
* You might want to include some suggestions on what to ask or how to use the copilot

### Key Demo Highlights
When demostrating a copilot in Copilot Studio, ensure it is highlighted that the first message can be dynamic, customized and personalized

# Get Started Below
It is fairly simple to just show the personalization aspect with copilots built with Copilot Studio by changing the standard text to custom text. 

Below is the YAML code for the standard Conversation Start topic. Update the text to include something more relevant and personalized

    kind: AdaptiveDialog
    beginDialog:
    kind: OnConversationStart
    id: main
    actions:
    - kind: SendActivity
      id: sendMessage_M0LuhV
      activity:
        text:
          - Hello, I'm {System.Bot.Name}, a virtual assistant. Just so you are aware, I sometimes use AI to answer your questions. How can I help?
        speak:
          - Thanks for calling, how can I help?
