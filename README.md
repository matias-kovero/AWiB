
## AWiB Workshop
Our task is to create an chatbot that allows the user to tell his updated company information by anwsering questions the bot asks. After that we send the infromation from the bot to our RPA (Robotic Process Automation).  
Our RPA then fetches correct information of the company from YTJ.fi and show the user if the information is valid from the bot.

#### Content
- [Assistant](#assistant)
- [Connecting Chatbot to BAW](#connecting-chatbot-to-baw)
- [Automation](#automation)
- [Summary](#summary)  

#### Prerequisites
[IBM Cloud](https://cloud.ibm.com) Account

## Assistant
In this part we create the **Chatbot** and edit it so that it sends the required information to the middleware(?)
 - [LAB 1: Cognitive Chatbot Basics](./1-Basics)
 - [LAB 2: Understanding Sentiment - Integrating Watson Natural Language Understanding](./2-Sentiment)

## Connecting Chatbot to BAW
 This connects the backends of the chatbot and RPA so that they can communicate together. With this we are able to send the inputs from the chatbot to RPA.  
 ``Sandra?``  
  ``BAW?? Write what it means at least the first time it is mentioned``  
 
## Automation
[Environment](https://bluedemos.com/show/2399)(?)  
Login to your ``Virtual Machine``, it might take a while for the VM to launch.  
``Skip updates if it ask you to do so.``  
- [LAB 3: BAW](./3-Baw)
- [LAB 4: RPA](./4-RPA)
  
You may now test to application.  
**Go** to your chatbot and answer the questions.
  
## Summary
