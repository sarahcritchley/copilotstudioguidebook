# Demo Fallback in Microsoft Copilot Studio
This page covers a short walkthrough on setting up Fallback behaviour for Microsoft Copilot Studio for demonstration purposes.

## Configure Fallback (Basic)
Understanding [Fallback basics](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Chapters/Fallback%20Basics.md) Microsoft Copilot Studio already has basic Fallback behaviour configured. This can be found in the standard out of the box topic called 'Fallback'. 

You can consider some basic customizations for your demostration so you can showcase how easy it is to configure and extend with capabilities that help showcase and promote positive user experiences beyond that provided out of the box.

1. Navigate to the system 'Fallback' topic. (If you are unfamilar with the product, it is recommended to backup the YAML code of system topics before configuring as you cannot rollback to the out of the box behaviour once changed)

2. Change 3 to 2 in the Conditional Check for Fallback Count. Fallback Count counts the amount of times a user concurrently hits fallback to prevent them getting stuck and having a poor experience

3. Add some relevant message variations based on your demostration

### Key Demo Highlights
It would be useful to ensure you highlight the following items when demostrating this feature:

* Fallback is available straight of the box and easily configurable using the low code studio canvas
* Fallback is important behaviour to configure and be able to provide good service to your users when a user has a question not covered in the copilot scope
* Discuss other examples mentioned in [Fallback basics](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/* I%20want%20learn%20how%20to%20build%20copilots/Chapters/Fallback%20Basics.md)

# Get Started Below
The YAML is below with the edits shown above of the Fallback Count number being changed to 2 and an additional message variation. This is the same sample used in the Fallback basics link and is easy to paste in and modify to suit your needs:

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


## Configure Fallback (Additional Examples Coming Soon)