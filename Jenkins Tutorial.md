# Jenkins Tutorial

[Step 1: Setting Up Your Project](#setting-up-your-project)

[Step 1.1: Creating a Folder](#creating-a-folder)

[Step 1.2 Creating a Jenkins Job](#creating-your-jenkins-job)

[Step 2: Running a Jenkins Job](#running-your-jenkins-job)

[Final Thoughts](#final-thoughts)

## Step 1:
## Setting up your project

### Creating a Folder

Each team should have their own folder in Jenkins.

To do so, first click the 'New Item' link on the side:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/NewItem.PNG)

A screen like the following will appear:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/NewItemName.PNG)

Enter a name, select the 'Folder' type and hit save on the bottom.

You should have been brought to another page like the following:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/NewItemName2.PNG)

Just click save on the bottom.


## Step 1.2
### Creating your Jenkins Job

To create a Jenkins Job click the 'New Item' on the side.

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/NewJenkinsJob.PNG)

Then give it a name and select 'Freestyle Project' and click 'Ok' on the bottom.

You should have been brought to a screen like the following:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/jobconfig.PNG)

This is your Jenkins Job configuration.

### Step 1.2a: Defining your SCM (Source Control Management) ie. Git:

Go down to to 'Source Control Management' in your job configuration and select git.

Then enter the URL to your repository and specify the branch you want to build, like the following:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/git.PNG)



### Step 1.2b: Achieving a clean Workspace:

Go to the 'Build Environment' section and check 'Delete workspace before build starts'. This way your workspace will always be clean with the newest material from your git repository. 

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/deletework.PNG)

If you don't do this, you might get a folder already exists error from the git step on your 2nd or more build since the repo folder is already there (because you haven't removed it).

### Step 1.2c: The Build Step

This step is the most important. It's the step where your project actually gets built.

Click 'Add Build Step' , like the following:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/addBuildStep.PNG)

Then select 'Execute shell' , you should see something like: 

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/shell.PNG)

You can treat this shell like your own, locally. Anything you want to do can be done in here.

ie, run mvn, python, java etc.

Commands are the same as you would type in locally as well. Below is an example of me checking the python version.

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/pythonVersion.PNG)

Once you have something to build, go to the bottom and hit 'Save'.

### Step 1.2d: Final Thoughts in Job Configuration:

In this section we have looked at grabbing your code from Source Control (ie Git) and then building the source code just like how you would build it locally.

Next we will run the job.

## Step 2:
### Running your Jenkins job

To run your Job, if you're on the highest level of Jenkins: Click on your folder, and then on your job.

On the side you should see 'Build Now' (Also notice that 'Configure' is there too, where all of step 1.2 happened), go ahead and click it.

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/buildNow.PNG)

Once you click Build Now, you'll start seeing your build history on the side:

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/history.PNG)

The blue denotes a successful build, the red denotes a failed build.

To see the output of the build, just click on the build number and then click 'Console Output':

![](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/Console.PNG)

From Step 1.2c  I put in 'python --version', therefore in my output I should see the output of that command.

And you can clearly see it's there:

![Drag Racing](https://github.com/ProfDema/UTMCSC301/blob/master/csc301-2020/Jenkins/images/console2.PNG)

# Final Thoughts

This is the basic workflow:

Write code locally.

Run/test your code locally.

Check in code to Github.

Run Jenkins job which will pull Github project and build your code.
