# Lab 2: Docker, Mayhemfile, and Reproducing Results

## Let's get started! 

One prerequisite to a fully autonomous appsec pipeline is to have a fully
reproducible build and replay environment. This guide will show you how to
reproduce the results from lab 1 on the UNIX CLI.  We will also give a basic
introduction to Docker.

**Time to complete**: About 20 minutes
  
Click the **Start** button to move to the next step.

## Get access to the Mayhem CLI

In addition to the web UI, Mayhem provides a CLI (command line interface) 
called `mayhem`.  You can always access the latest CLI from the 
[Mayhem server](https://training.forallsecure.com/-/installation). 

To install it, run:
```
    curl -o mayhem https://training.forallsecure.com/cli/Linux/mayhem &&
    chmod +x mayhem &&
    sudo mv mayhem /usr/local/bin/
```

**Tip**: Click the copy button on the side of the code box and paste the 
command in the Cloud Shell terminal to run it.

## Log into Mayhem from the CLI and sync results

The `mayhem` CLI talks to the Mayhem server via an API token.  You need
to get your API token to log in, which can be found either from
the [download screen](https://training.forallsecure.com/-/installation).
You can manage API tokens from your profile.


```
mayhem login https://training.forallsecure.com/ <YOUR API KEY>
```

**Tip**: You can always find your API token under the "?" on the Mayhem UI as well.


## Download results

You can download all results from the Mayhem server using the CLI.

```
mayhem download forallsecure/lighttpd -o /tmp/lighttpd
```

   * To see targets to download, you can do a `mayhem list`
   * Use `-o` gives the output directory.

Go see the results in `/tmp/lighttpd`

**Tip**: You can use the `mayhem sync` command to syncronize
a folder that already has a `Mayhemfile`.

## Run docker image to reproduce results

Docker is a lightweight container, which is like a virtual 
machine but at the UNIX process level. While a full docker
tutorial is out of scope here, we show you here some basic
nuts and bolts. 


To run the vulnerable image:
```
docker run --rm -i -d -p 8080:80 forallsecure/lighttpd:vulnerable
```

This command:

  * Runs the docker image `forallsecure/lighttpd:/vulnerable`
  * The `-p` binds port 80 in the docker image to localhost port 8080
  * The `--rm` removes any temporary state when the
    container exits.
  * The `-d` says to run in daemon mode, i.e., as a background 
    process.

To check that the docker image is running, run the `docker ps` command:

```
docker ps -a
```



Since this is a network server, we will use a utility called
`nc` (netcat) to connect to the server and feed Mayhem output.

To install `nc`, run:

```
sudo apt-get install -y netcat
```

Then to replay a test case, simply `nc` to localhost port 8080:

```
nc localhost 8080 < /tmp/lighttpd/corpus/ba0dbafbd0b787a564635b887f77926ae0b3f979dcc72d30cf7fdb1707581919
```

If you replay the exploit, then you should see the image exits with:

```
docker ps -a
```

## Challenge: run docker with the corpus mounted

**Challenge:** run docker in interactive mode with the corpus mounted under
`/mnt`. To do so, you'll need a couple of other CLI options:

  * The `-it` option runs docker in interactive mode with a user-given
    command. For example:
```
docker  run -it forallsecure/lighttpd:vulnerable bash
```
  * The `-v` flag will mount the local file system. For example:
```
docker -v /tmp/lighttpd/corpus:/mnt forallsecure/lighttpd:vulnerable
```



## Congratulations

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>

You've just replayed your first exploit.
