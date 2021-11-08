# Lab 2: Docker, Mayhemfile, and Reproducing Results

One prerequisite to a fully autonomous appsec pipeline is to have a fully
reproducible build and replay environment. This guide will show you how to
reproduce the results from lab 1 on the UNIX CLI.  We will also give a basic
introduction to Docker.

**Time to complete**: About 20 minutes
  
Click the **Start** button to move to the next step.

## Get access to the Mayhem CLI

In addition to the web UI, Mayhem provides a CLI (command line interface) called
`mayhem`.  You can either:
    * Install it onto your local computer (Linux and OSX supported) from the
      [Mayhem server](https://training.forallsecure.com/-/installation). 
      *Hint: You can always find the CLI underneath your user account.*
    * Install it within the cloud shell.
    ```bash
    curl -o mayhem https://training.forallsecure.com/cli/Linux/mayhem &&
    chmod +x mayhem &&
    sudo mv mayhem /usr/local/bin/
    ```
    
** Backup Solution: If you get lost, we also provide a pre-configured cloud
shell.** 
