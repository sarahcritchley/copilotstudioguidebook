--

*NOTE: These pages are aimed to be part of the role based guidance at the top level of this documentation, specifically aimed at professionals trying to move towards a particular outcome. They will refer and act as pointers to our official product documentation. The official product documentation will go into much more feature detail than the specific tutorial where they are referenced.

--

# What is Disambiguation in Microsoft Copilot Studio
Disambiguation means to try and figure out what the intent was out of a group of one or more conflicts. As a human being, you would have experienced disambiguation scenarios yourself when you have asked another person for clarification on what was meant. You did this to gain additional clarity on the intent of what that person said to you can better meet their needs. 

Let's go through an example:

* *Person 1 to Person 2*: Can you please get me a drink

* *Person 2*: Did you mean coffee, tea or something else?

To disambiguate essentially means to clarify, and in the example above the disambiguation experience is the clarifying answer from Person 2. They didn't answer the question but it is a building block to be able to answer the question and to clarify intent.

In Microsoft Copilot Studio, Disambiguation behaviour is built in to manually authored topics. 

Disambuguation is visible in the studio under the system topic called 'Multiple Topics Matched', as shown below

## What problem does it solve?
Disambiuation solves the problem of processing or assuming an incorrect intent from a question. By dismbiguating and asking clarifying questions it means the confidence of correctly matching the intent of a user is higher and the question is answered or processed which has the most appropriate outcome. 

Ideally of course, correctly matching the intent of a question without asking clarifying questions through a dismbiguation process is the most ideal scenario. Disambugation questions are meant to catch ideally a small set of experiences where there could be closely matching intents, and rather than answer incorrectly, it is more appropriate to ask a clarifying question. 

In your conversational experiences there are also typical thredholds of the number of clarifying questions that should be asked at any one time. This is so you do not end up in a loop or cycle of clarifying questions which would be a negeative experience for a user and can clearly process next level escalation behaviour should an intent not be able to be understood. 

# How to use it
As mentioned, disambuguation functionality is visible in the studio under the system topic called 'Multiple Topics Matched', as shown below

![Image of disambiguation topic](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Disambuguation-Topic.png?raw=true)

If there are one or more closely matching topics based on a user's question, this topic will be ran and it displays a list of those closely matched topics and asked the user to select if any of those topics were relevant to the question.

Makers can open this system topic and where required, even modify this topic. Modifying system topics should not be done without having a good understanding of the studio and always ensure you make a backup of the YAML before making any changes, so you can revert back to the original if needed.

An example of modifying this topic is removing an option from the list of topics presented to a user when this topic is reached.

To learn more about Trigger Phases in Microsoft Copilot Studio and avoiding having to use disambuguaton, check out the page on best practices with Trigger Phrases here: https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/trigger-phrases-best-practices

A page on to modify the disambiguation topic will be coming soon