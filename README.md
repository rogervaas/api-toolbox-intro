# BitScoop API Toolbox Intro

This demo is a quick tour of how to configure the BitScoop API Toolbox to interact with "data providers" such as Google, Facebook, Salesforce, and GitHub, and the APIs they publish. As part of this tutorial we'll be:

  1. **Setting up a local development environment.**
  2. **Getting an API key for BitScoop.**
  3. **Creating Provider Maps on the BitScoop API Toolbox to interact with APIs.**
  4. **Learning how to create Connections to deal with 3-legged authentication and authorization.**

As part of this demo, we'll be running our own mock "data provider," which will give you an opportunity to view the requests that the BitScoop API Toolbox makes in real time and in more granular detail.
You'll need to run the local server and temporarily publish it so that it's available publically and the API Toolbox can reach it.

We'll be using a few key technologies that you'll want to familiarize yourself with before we get started.
Please note that while we use these external technologies ourselves, we CANNOT OFFICIALLY ENDORSE THEM NOR BE HELD RESPONSIBLE for any issues with respect to security, etc. that you may encouter while using them.

Be sure to verify your downloads whenever possible using checksums or signatures to ensure their authenticity and origin especially if you're working with sensitive information.

After getting set up with these technologies, we'll walk you though creating a Provider Map on the BitScoop API Toolbox and will build up an example step-by-step.
Finally, we'll direct you to a more practical Provider Map that deals with a 3-legged authentication workflow.


## First things first, pre-requisites!

### NodeJS

The mock data provider is written in Express on top of NodeJS.
You'll need to install NodeJS if you don't have it already.
You can find the latest versions here [https://nodejs.org/en/download](https://nodejs.org/en/download).
The installation instructions for each platform are out of scope of these instructions, but you'll generally want to make sure that the `node` and `npm` (bundled with NodeJS) executables are on your path.
You can test to see if everything is working by running:

```
node --version
npm --version
```

If you get version numbers for both, then you're in business.

### git

You don't technically need Git installed to finish this demo, as you can download and extract the bundled files directly from GitHub.
However the instructions here will assume that you're running with Git.
If you're on Windows or MacOS you can install [Sourcetree](https://www.sourcetreeapp.com/) published by Atlassian, which comes with an embedded Git binary.

### ngrok

ngrok is a great tool for software developers that allows you to push local ports to temporarily available public URLs.
If you're familiar with SSH remote port forwarding, this concept probably won't seem new to you.
However the advantage of ngrok over plain SSH forwarding is the automatic provisioning of the public URLs and the fact that you don't need to configure any infrastructure yourself.

ngrok is a simple binary that you can download from [https://ngrok.com/download](https://ngrok.com/download).
Make sure you add the binary to the path.
You can test to see if everything is working by running:

```
ngrok --version
```

Note that if you'd prefer to plain SSH remote port forwarding, you'd certainly be able to do so, but you'd need to adapt some of these instructions accordingly.
Any instructions hereafter assume that you're working with ngrok.

Note that if you're using the free tier of ngrok you'll be limited to about 40 requests per minute.
This won't typically be a problem for this introduction, however if you notice an error returned from the BitScoop API Toolbox indicating a rate exceed error referencing an ngrok limit, that's what's going on (i.e. it's not us throttling you).

### Postman

Postman is a Chrome app that lets you construct detailed HTTP requests and easily read and understand the responses.
Think of it as an interactive `curl` for humans. That said, if you want to use `curl` we won't stop you!

If you have Chrome installed you'll want to grab Postman from the [Chrome store page](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop).
If you don't have Chrome installed you'll probably want to install it, but the installation instructions are out of scope of this demo.


## Clone and set up this repository

You'll want a local copy of this repository.
There are clone instructions right on GitHub, but generally just run:

```
git clone https://github.com/bitscooplabs/api-toolbox-intro
```

Once you have the code locally change directory into the server directory and install the project requirements with `npm`.

```
cd server
npm install
```


## Get logged into BitScoop

OK, now that you're hopefully rolling with the programs you need, we're going to *actually* get started.
First you'll need to log into BitScoop at [https://bitscoop.com/login](https://bitscoop.com/login).
If you don't yet have an account you can request a signup code at https://bitscoop.com/api-toolbox-beta-request.
The wait isn't prohibitive, for the time being we just want to send you an email before you get on our system.

Once you're logged in, head to the API Toolbox at [https://developer.bitscoop.com](https://developer.bitscoop.com).


## Diving into Provider Maps

Within the BitScoop API Toolbox, a Provider Map is a JSON configuration that controls the interactions with a data provider.
We've put together a few steps that we want to take you through to build up a Provider Map that interacts with your local development data provider.
Finally we wanted to send you off with a real world example of how you might use BitScoop to power a GitHub application.

We've broken apart the tutorial steps so that this README didn't get prohibitively (or uninterestingly) long.
While you don't necessarily need to do the steps in order, the content therein has been written with that assumption.

Check out the tutorial here: [https://github.com/bitscooplabs/ngrok-demo/tutorial](https://github.com/bitscooplabs/ngrok-demo/tree/master/tutorial).
