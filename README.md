# CICDLabsHOL

Create a project on [VSTS](https://www.visualstudio.com/team-services/)

![D1.png][1]
---
Name the project and add description. Also choose the Git as your version control type.

![D2.png][2]
The project will be create and you will have option to push code or import existing repository.

![D3.png][3]
---
Select import a repository and Clone URL https://github.com/krishnaji/lets-chat.git

![D4.png][4]
---
You should see message Import successful
![D5.png][5]
---
Now once the repository is imported , its time to setup a new Build.
![D6.png][6]
---
In search box find and add following tasks.
- npm
- grunt
- Achive files
- Copy and publish build Artifacts

![D7.png][7]
---
Rename the buld letschat-CI and select the Agent as Hosted VS2017

![D8.png][8]
---
Now we have to configure each task. Lets start with npm. Set npm task as shown in image.

![D9.png][9]
---
Set Grunt task as shown in image

![D10.png][10]
---
Set up Archive Files task as shown in image below.

![D11.png][11]
---
Setup the Copy and Publish task as show in image below.

![D12.png][12]
---
Now save(only) the build definition. Do not queue for now.

![D13.png][13]
---
Select / as your save build definition folder.

![D14.png][14]
---
Now its time to queue the build.

![D15.png][15]
---
Select Agent as Hosted VS2017

![D16.png][16]
---
You can view the running build.

![D17.png][17]
---
You should see running tasks.

![D18.png][18]
---
Once the build is completed you should see Build Succeeded message.

![D19.png][19]
---
Now lets create a release. 

![D20.png][20]
---
Rename the release definition name.

![D21.png][21]
---
Add artificat by selected Add artifact.

![D22.png][22]
---
Now add new enviroment 

![D23.png][23]
---
Name it Stage

![D24.png][24]
---
Click Add doprdown and clone the enviroment.

![D25.png][25]
---
Name the new cloned enviroment as Production

![D26.png][26]
---
Add variables  these will be refredn in Stage and Production task configuration

![D27.png][27]
---
Add two vriables as shown below. Select Release as Production and Stage for respective variables. Note the website name is set to your app service name and stage is the Stage slot.

![D28.png][28]
---
Now select Stage Task and add Azure App Service Deploy task. Refer below image.

![D29.png][29]
---
We will first depoy the app to the slot named Stage.Configure the app service deploy task. Select the Azure subscriotion and Authorize it. 
Seet the app service name as the variable that we created. Also check the Deploy to slot box.
**Note:** If you get error, open VSTS link incognito or private browsing mode and create Azure Resource Manger Endpoint. Please refer this [link](https://docs.microsoft.com/en-us/vsts/build-release/concepts/library/service-endpoints)

![D30.png][30]
---
![D31.png][31]
---
Now select Production task and configure it to sawp the production and stage slots.
Save it.

![D32.png][32]
---
Create a new rlease.

![D33.png][33]
---
Select all enviroments.

![D34.png][34]
---
Visit the release 

![D35.png][35]
---
Depoly Stage manually.

![D36.png][36]

![D37.png][37]
---
You should refer the logs for details about the release task execution.
The Stage should be successful. Once done you can browse `http://<WebAppName>-<SlotName>.azurewebsites.net` stage app.

![D38.png][38]

Now like stage Deploy the the Production. Once its done you should see the slots are swapped. Visit `http://<WebAppName>.azurewebsites.net` to verify it.

[1]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D1.png
[2]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D2.png
[3]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D3.png
[4]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D4.png
[5]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D5.png
[6]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D6.png
[7]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D7.png
[8]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D8.png
[9]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D9.png
[10]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D10.png
[11]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D11.png
[12]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D12.png
[13]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D13.png
[14]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D14.png
[15]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D15.png
[16]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D16.png
[17]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D17.png
[18]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D18.png
[19]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D19.png
[20]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D20.png
[21]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D21.png
[22]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D22.png
[23]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D23.png
[24]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D24.png
[25]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D25.png
[26]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D26.png
[27]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D27.png
[28]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D28.png
[29]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D29.png
[30]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D30.png
[31]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D31.png
[32]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D32.png
[33]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D33.png
[34]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D34.png
[35]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D35.png
[36]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D36.png
[37]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D37.png
[38]:https://github.com/krishnaji/CICDLabsHOL/blob/master/D38.png
