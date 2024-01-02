--

*NOTE: These pages are aimed to be part of the role based guidance at the top level of this documentation, specifically aimed at professionals trying to move towards a particular outcome. They will refer and act as pointers to our official product documentation. The official product documentation will go into much more feature detail than the specific tutorial where they are referenced.

--

# What is Fallback in Microsoft Copilot Studio
In Conversational AI, 'fallback' refers to the behaviour when the system has to 'fall back' and does not know the answer to the question being asked. 

This behaviour is essential in every conversational experience in some form, because a copilot will not be able to answer every single question a user may have. A user of your copilot should be expected to ask a question not covered in the scope of your copilot, and so you should always consider when designing your copilot what behaviour should occur in this scenario. This would be your fallback configuration.

This behaviour can be seen in Microsoft Copilot Studio through the system topic called 'Fallback'. This topic can be called manually from an authored topic and the conversation flow routed to this Fallback system topic, or it will be automatically called by the system if there are no matching authored topics and Generative AI features are either not configured or no relevant information or data is found which is found, based on the feature, to be appropriate. This trigger is a system trigger called 'on unknown intent' because the intent is unknown. 

This system topic comes with prebuilt behaviour where it keeps a count of how many times it has been triggered and if this is below 3, it will display a message "I'm sorry, I'm not sure how to help with that. Can you try rephrasing?". Once it reaches 3, it will direct to another system topic of 'Escalate' and complete the behaviour within that system topic.

## What problem does it solve?
Fallback behaviour solves a negative user experience problem. Where fallback behaviour is not configured, it can be fustrating if a user is asking a question and the copilot either doesn't respond or responds with information not related to the question. 

It also solves the problem of scope. As mentioned above, a copilot will not be able to answer every single question in the planet that a user asks, it will be limited to the designed scope of the copilot. By having basic Fallback behaviour built into the copilots by default and configurable via the Copilot Studio interface it means this behaviour can be easily added and customized.

# How to use it
The Fallback system topic already comes with default behaviour, however you may want to configure it to meet your needs.

Some examples of typical fallback behaviour customizations include:

* Changing the number of tries in the FallbackCount number e.g. reduce this number to 2
* Change the message to include something specific to your orgainization
* Add more than one message varitions to the message to sound more natural 
* Change the 'Escalate' redirect to send an email to a DL instead
* Change the 'Escalate' redirect to log a support ticket in a relevant system and let the customer know the returned Case or Ticket Number

Below you can see the FallbackCount number has been changed to 2, and also includes more message variations:

![Image of fallback topic](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Fallback-Customized.png?raw=true)

# Get Started Below
The YAML is below with the edits shown above of the Fallback Count number being changed to 2 and an additional message variation:

    kind: AdaptiveDialog
    beginDialog:
    kind: OnUnknownIntent
    id: main
    actions:
        - kind: ConditionGroup
        id: conditionGroup_LktzXw
        conditions:
            - id: conditionItem_tlGIVo
            condition: =System.FallbackCount < 2
            actions:
                - kind: SendActivity
                id: sendMessage_QZreqo
                activity:
                    text:
                    - I'm sorry, I'm not sure how to help with that. Can you try rephrasing?
                    - |
                        Apologies, we don't seem to cover questions around that topic. Could you rephrase?

        elseActions:
            - kind: BeginDialog
            id: 5aXj5M
            dialog: crf24_copilotGuideSamples.topic.Escalate