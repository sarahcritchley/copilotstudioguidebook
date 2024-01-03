# Demo Generative Answers in Microsoft Copilot Studio
This page covers a short walkthrough on setting up Generative Answers for Microsoft Copilot Studio for demonstration purposes.

## Configure Generative Answers
To configure Generative Answers, this can be done when you first create your copilot. It can also be completed from existing copilots by navigating to the 'Generative AI' section on the sitemap. 

![Image of Enabling Generative Answers Sitemap](https://github.com/sarahcritchley/copilotstudioguidebook/blob/main/I%20want%20learn%20how%20to%20build%20copilots/Images/Customize-Generative-Answers-Enable.png?raw=true)

The fastest way to get started to demostrate the capabilities is to enter a public facing website as the data source. 

Remember Generative Answers can be surfaced in two ways with Copilot Studio:

* Copilot Scope: Configured under the 'Generative AI' section of the sitemap 
* Topic level Scope: Configured using the 'Generative answers' node within 'Advanced' in the authoring canvas

Setup Generative Answers at the Copilot Scope by going to the website you want to enter e.g. microsoft.com and take a look at what type of information is on the website. Is there useful information on the website? Some of the best websites are FAQ type websites that are information rich and contain text based information.

Think about questions which can be answered from the information stored within this page. For example, the Mirosoft website contains information about products Microsoft sells. This includes Laptops to Xbox. I can consider asking questions such as 'What products do you sell?' or 'What laptops do you sell?'.

In Microsoft Copilot Studio, add the website in the configuration page for Generative AI, and save the page. Wait a few moments and you should now be able to ask questions based on information on the website you entered. Ask a number questions you want to showcase before and confirm how relevant the answers are and if they answer your question.

It is recommended you iterate a few times based on the time you wish to invest in exploring this feature to determine the scope of the questions based on the data stored within the website you enter.

### Key Demo Highlights

It would be useful to ensure you highlight the following items when demostrating this feature:

* Speed to setup with a public facing websites
* Highlight additional datasources e.g. Sharepoint, Onedrive & File upload
* The output of the responses
* The behaviour of the system where it checks if a manual topic exists first matching the question, and if one does not exist, the copilot Generative Answers behaviour is activated to see if the connected datasources contain relevant data that can be summarized into a response
* If Generative Answers (at Copilot Level) does not have a response, the fallback system topic is triggered (which can be customized)

### Considerations
It is important to consider how Generative Answers works, and so it is recommended you read this page here to be able to discuss those basics.

Additionally, discuss with your team about the considerations when using Generative AI, including Generative Answers. When you are helping our customers discover the capabilities of a product, there are different facets and topics to determine what could be the most appropriate route. Since data and information are critical when it comes to Generative AI and connecting Microsoft Copilot Studio to that data, having conversations around existing sources of information they wish to use, what is the input is for that data source, how the results are formatted, how the information is curated, by whom, when it gets updated and also security requirements.

