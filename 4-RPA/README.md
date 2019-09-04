## Welcome to the RPA workshop
If the other sections where mainly reading and viewing already done elements, now you will get to create your own working bot with _Robotic Process Automation_ platform (IBM RPA with Automation Anywhere).  

What this ``bot`` should do:
1. Waits for a task assigment (Get info from YTJ) from the workflow (Handle data change) that is triggered from our _Cloud Functions_ within our Watson Assistant chatbot.
2. Receives the business_id (y-tunnus) from the workflow.
3. Navigates to _ytj.fi_ web site and creates a search with the given business_id.
4. Gathers the address information from the search result.
5. Sends the gathered information back to our workflow that automatically forwards it to the next task in the workflow (User validation).

#### Content
- [Setup](#setup)
- [Launch RPA](#launch-rpa)
- [Robot Framework location](#robot-framework-location)
- [Editing the robot](#editing-the-robot) 
- [Coding the bot](#coding-the-bot) 
- [Help](#help)

### Setup
**Check** that the RPA is running by opening __Chrome__ web browser and opening ``RPA Control room`` from the bookmarks under RPA-folder. You should see this page (No need to login, just check that the page loads). If not, ask your instructor to help you.

![](./images/RPA_ControlRoom.png)  

### Launch RPA
Open the __TOOLS__ folder from your desktop and double click __AA Enterprice Client 11.3__ to open our RPA editor.

![](./images/RPA_Launch.png)

After that login  with ``username`` (__developer__) & ``password`` (__adminadmin__).

![](./images/RPA_Login.png)   

It might prompt you with a pop-up - if so, select __Skip__ from the bottom-right. 


### RPA implementation artifacts
We have already created a skeleton implementation for you to get started. Move to __AWiB__ folder by clicking the folder from the Task navigation area on the left-hand side under My Tasks. The contents of the AWiB folder will be shown within the editor.

**!!** **If you double-click a file it will run it.**  **!!** So, DO NOT run these unless told in these instructions.

``You can edit the file by clicking it once and select edit from the top or right-click and select edit.``

![](./images/rpa_artifacts.png)

Files in this directory:  
**Get info from YTJ**   
This is our main RPA task bot that will be run, when our workflow will be started and when RPA task (Get info from YTJ) is triggered. Notice, that this task bot is named exactly like our RPA task in our workflow. This task bot was generated using the bot definition file downloaded from the workflow.

**Loop over IBM Business Automation Workflow tasks**  
This is what we call a "system bot". When this is started, it automatically connects to workflow environments to check if there are some RPA tasks waiting to be done and if so, it will run ``Get info from YTJ`` task bot. The system bot is provided by the RPA platform, so you do not to build it yourself. Once it's started, it is configured to poll our workflow environment from time to time and when it finds something to do, it will run the main task bot (Get info from YTJ in our scenario).

**YTJ implementation** . 
This is the task bot that we will be implementing the actions needed to gather the date from ytj.fi web site. ``Get info from YTJ`` calls this task bot. In other words, we could have implemented the needed robotic actions directly Get info from YTJ -bot, but this way it is a bit more feasible to work, separating the actual implementation from the generated main bot.

### Editing the robot
Open the _YTJ implementation.atmx_ to __editor window__ (right-click --> Edit).

On the left you will see a list of configurable commands that you can use. First, We will need ``Open Browser`` (found under Web Recorder) & ``Object Cloning``. Feel free to explore other commands as well. IBM RPA with Automation Anywhere offers over 600 different, easily configurable command to build your RPA bots.

If you double-click a command it will be added to your bots Action List. If you add something by accident, you can delete a command by right-clicking it and selecting "Delete".

On the right-hand side you will see a few bars, we are intrested on ``Variable Manager``. Click on it to expand it.

Here we have defined a few variables you will need:  

``business_id``, the business_id (y-tunnus) that our customer originally told to our chatbot.  
``street_address``, here we will save the info we get from ytj.fi   
``postcode``, here we will save the info we get from ytj.fi
``city``, here we will save the info we get from ytj.fi
   
#### Implementing the bot
__1.__ To start off, drag and drop ``Open Browser`` command to your Action List, just below __the first comment line__. Drop the command __on the__ 1st comment line and it will be added below it. You can also click once to select the 1st comment line and when it is selected, __double-click__ the "Open Browser" command from the command list and it will be added under the selected comment line.

![](./images/command1.png)

When the Open Browser configuration window opens, type in ``https://www.ytj.fi`` to "Step 1: URL to Open" and click __Save__.

<img src="./images/conf_openbrowser.png" width="50%">

You can now test and run your bot for the first time! It has only one command - to open YTJ web page in web browser -, but let's run it because we need the YTJ web page opened when we move forward. First, click __Save__ on the editor window and then __Run__ to test your bot. __NOTE!__ When you click "Run", the RPA platform will take over your controls (mouse and keyboard). Make sure not to touch anything when the bot is running or you might interfere its operation.

![](./images/start_stop.JPG)

Your bot should run and YTJ web page should be opened in Internet Explorer (IE). Bot stops automatically. If you see a pop-up in IE about some security preferences, click "Ask me later" to close the pop-up. Nice! Your first RPA run :) __Make sure to leave the YTJ web site open!!__

__2.__ Next lets add a ``Object cloning`` and select the search box from the ytj.fi website. We will add the business_id variable value to it.

- Back in RPA editor window, drag and drop ``Object Cloning`` command under the second comment line.
- When the configuration window opens, select "YTJ - Etusivu - Internet Explorer" for the Select Window -configuration.
- Next click __Capture__ button __and keep your mouse button pressed down!__
- While keeping your mouse button down, you should now see the YTJ web page in IE. __Move your mouse cursor over the search input field__ (Hae yrityksen nimellä tai Y-tunnuksella) and when you see a red rectangle pulsing around its borders, let go of your mouse button. This will capture the text input field as an object that we can next define some actions against.
- When the configuration window opens, select __Set Text__ to "Select action to perform".
- Click "Text to set" input field to move your cursor/focus to it.
- Press __Function + F2__ [Fn+F2] 

![](./images/select_searchBar.gif)

__3.__ We will want to next press the search button.  
![](./images/pressSearch.gif)  

__4.__ Now go and press the search button manually. We need to get to the next page for the next task.

__5.__ The robot needs to click the first search result.  
![](./images/clickFirstLink.gif)  

__6.__ Now go and press the first seacrh result manually. We need to get to the next page for the next steps.

__7.__ We Want to get the name of the company
![](./images/selectName.gif)

Please check you have the values like so:  

  
![](./images/nameValues.png)   


__8.__ We need to select the position of postiosoite  
![](./images/selectPostiosoite.gif)  

Please check you have the values like so:  
  
  
![](./images/postiosoiteValues.png)  

__9.__ Setup our function that gets dynamically our ``street_address``, ``postcode`` & ``city``  
![](./images/setupFunction.gif)

##### Help
I can't select ytj.fi to my ``Object clone``   
> Please check you have the webpage open on the background. As it will list only pages you have open.  

How to add variables to fields?  
> Select the field you want the variable and press F2 . 

Robot isn't doing nothing  
> Make sure you don't have multiple webpages open, it will only work on one page.  

Web page stays open after task is completed  
> Remeber to add a close webpage at the end of all code blocks  

I'm stuck, what to do.  
> Don't hesitate to ask help.   

> Also if you can't get the functions to work. There is an working version. Ask assistance to get it setup.  
