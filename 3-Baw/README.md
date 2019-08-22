## Welcome to the BAW workshop
Here we will explore BAW and view a few of its capabilities.
#### Content
- [Access to BAW](#access-baw)
- [Finding the workflow](#finding-the-workflow)
- [Quick guide on workflows](#quick-guide-on-workflows)
- [Editing workflows](#editing-workflows)  
#### Access BAW
Open chrome and navigate to **BAW** Login, fill in the ``username`` & ``password``
![](./images/BAW_Login.png)
#### Finding the workflow
**Select** AWiB Workflow
![](./images/BAW_Workflow.gif)
#### Quick guide on workflows
This workflow has 3 lanes, **RPA**, **Handler** and **System** (these lanes are user defined so you can name them whatever you like)  
![](./images/BAW_Design.png)  
In this particular workflow:  
- **RPA** Is responsible of the robot actions.  
It takes values from the ``start`` node (values we sended from Watson assistant)  
and performs our ``Robot task`` that you will create.  
- **Handler** lane has an ``Validate data`` node.  
We have defined it to be a form. This form will show the information we got from the ``start`` node and the information from the ``Robot task`` node.  
The user has to review the information and decide if the information is valid.
- **System** lane has a few nodes in this setup.  
These nodes are completely demostrative for this workshop, but we have given a few examles you could do after the user has validated the data.  
If the data is valid, we could save the updated data to an CRM alternatively we could inform the customer that we couldn't update the information.   
#### Editing workflows
By clicking a node in the workflow, you are able to view and edit its functions.  
![](./images/Robot_Info.png)   
Settings we need to edit on the ``Robot task``:  
- **General** Give name and color. 
- **Implementation** Here you choose the type of the node, and if it is an ``Robot task``you will need to press **Generate bot...** to create an framework where you can later on implement the actions of the bot.  
- **Data Mapping** If the robot uses additional information we need to provide them to it. Here we map the data to parameters so that the bot is able to use it.

When you open an form node, you will have a new workflow where you define what the form does when you interact with it.
![](./images/Form_Workflow.gif)  
We have defined that it will send forward to the next node __true__ or __false__ depending on what the user has pressed.  

Feel free to explore the diffrent nodes and options on this workflow. Remember to to **Generate Bot...** on the ``Robot task`` node (Implementation tab).