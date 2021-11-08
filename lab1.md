# Lab 1: Your first run. 

## Let's get started!

This guide will show you how to get started with Mayhem and fuzz your first
application!

**Time to complete**: About 10 minutes

Click the **Start** button to move to the next step.

## Create a Mayhem account

![Mayhem Account Creation](https://raw.githubusercontent.com/dbrumley/fuzzing-cloudshell-tutorial/master/assets/images/account-creation.png)

Create a new account by navigating to 
[training.forallsecure.com](https://training.forallsecure.com) and either choose:
   * Google account: Use your Google account on Mayhem
   * "Sign up": Create a local account on the Mayhem instance. 

## Create a new Project

We will be analyzing an existing DockerHub image we've created that has a
vulnerable version of [lighttpd](https://www.lighttpd.net/) (version 1.4.15, to
be specific).

   * Create a new project by clicking the "plus" icon at the top of the screen.
![Create new project](https://raw.githubusercontent.com/dbrumley/fuzzing-cloudshell-tutorial/master/assets/images/create-new-project.png)
   * Select the DockerHub option, and then type in 
   ```forallsecure/lighttpd:vulnerable``` as the image name.
![Choose dockerhub
   image](https://raw.githubusercontent.com/dbrumley/fuzzing-cloudshell-tutorial/master/assets/images/project-from-dockerhub.png)

## Set the Basic Configuration Options

Set the analysis time at 30 seconds. This configures the active analysis (not
the total run time** to be 30 seconds.  

![Set Basic Analysis Options](https://raw.githubusercontent.com/dbrumley/fuzzing-cloudshell-tutorial/master/assets/images/basic-configuration-options.png)

**If you forget to set this value, runs will go forever**

## Set the Advanced Configuration Options

Navigate to the "Advanced" tab, and set two advanced options for this run:
   * Advanced triage. As we will see, this enables deeper analysis on each
     input. 
   * Code coverage. This will enable Mayhem to collect code coverage statistics.
   
![Set Advanced Analysis Options](https://raw.githubusercontent.com/dbrumley/fuzzing-cloudshell-tutorial/master/assets/images/advanced-configuration-options.png)

## Click start run!

Click the start run button at the bottom of your screen to begin analysis!

![Click start run](https://raw.githubusercontent.com/dbrumley/fuzzing-cloudshell-tutorial/master/assets/images/start-run-button.png)

## Congratulations

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

You've just replayed your first exploit.
