
## AWiB Workshop
### Use case
Corporate customers contact details have changed. To avoid any issues on future deliveries from their key Supplier, customer initiates contact details changes via Suppliers self-service.

Supplier utilizes AI to collect changed information from Corporate customer in a chatbot dialog. After all valid information has been collected (company name, address, phone number, etc...) - chatbot initiates a business workflow that orchestrates the actual information change into Suppliers system.  

Workflow utilizes both automated and manual tasks to finalize the contact details change. Robotic Process Automation (RPA) is used to supplement and validate company details given by customer from ytj.fi service.  
All contact and validation information collected during the process (company name, address, phone number, Business ID, etc...) are provided to workflow handler in modern UI, where handler can check the information provided by the customer matches the one got from ytj.fi and then decide to accept or decline the new address information.

#### Content
- [Assistant](#assistant)
- [Connecting Chatbot to Business Automation Workflow](#connecting-chatbot-to-baw)
- [Automation](#automation)
- [Summary](#summary)  

#### Prerequisites
- [IBM Cloud](https://cloud.ibm.com) Account
- Access to IBM Cloud image with [IBM RPA](https://www.ibm.com/automation/software/rpa) and [IBM BAW](https://www.ibm.com/products/business-automation-workflow) installed


## Assistant
In this part we create the **Chatbot** and edit it so that it can communicate with Cloud Functions.
 - [LAB 1: Cognitive Chatbot Basics](./1-Basics)

## Connecting Chatbot to Business Automation Workflow (BAW)
 This connects the backends of the chatbot and RPA so that they can communicate together. With this we are able to send the inputs from the chatbot to RPA. 
  - [LAB 2: Integrating RPA with Watson Assistant](./2-Functions)    
 
## Automation
[Environment](https://bluedemos.com/show/2399)(?)  
Login to your ``Virtual Machine``, it might take a while for the VM to launch.  
``Skip updates if it ask you to do so.``  
- [LAB 3: Business Automation Workflow](./3-Baw)
- [LAB 4: Robotic Process Automation](./4-RPA)
  
You may now test to application.  
**Go** to your chatbot and answer the questions.
  
## Summary
- [LAB 5: Our system in action](./5-Summary)
