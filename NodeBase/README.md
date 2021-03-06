# Selenium Grid Node Base

_This image is not meant to be run directly!_ It serves as the base image used for Selenium Nodes.

## Dockerfile

[`selenium/node-base` Dockerfile](https://github.com/SeleniumHQ/docker-selenium/blob/master/NodeBase/Dockerfile)

## How to use this image

First, you will need a Selenium Grid Hub that the Node will connect to.

```
$ docker run -d -P --name selenium-hub selenium/hub
```

Once the hub is up and running will want to launch nodes that can run tests. You can run as many nodes as you wish.

```
$ docker run -d --link selenium-hub:hub selenium/node-firefox
```

## What is Selenium?
_Selenium automates browsers._ That's it! What you do with that power is entirely up to you. Primarily, it is for automating web applications for testing purposes, but is certainly not limited to just that. Boring web-based administration tasks can (and should!) also be automated as well.

Selenium has the support of some of the largest browser vendors who have taken (or are taking) steps to make Selenium a native part of their browser. It is also the core technology in countless other browser automation tools, APIs and frameworks.

See the Selenium [site](http://docs.seleniumhq.org/) for documation on usage within your test code.

## Known Issues

### Problems with `/dev/random`

You may occasionally see that nodes will not immediately connect with the hub. In some cases the delay has been as high as 40 minutes. This is due to a known problem with linux containers where there is a lack of entropy within the running container. [James Bayer](http://blog.pivotal.io/cloud-foundry-pivotal/features/challenges-with-randomness-in-multi-tenant-linux-container-platforms) wrote a great article explaining the core of the problem.


You can either install an entropy gathering daemon (EGD), such as [HAVEGED](http://www.issihosts.com/haveged/index.html), on you docker host.

-- or --

Run your container with the `-v /dev/urandom:/dev/random` option. ie:

```
$ docker run -d -v /dev/urandom:/dev/random --link selenium-hub:hub selenium/node-firefox
```

## License

View [license information](https://code.google.com/p/selenium/source/browse/COPYING) for the software contained in this image.

## Getting Help

### User Group

The first place where people ask for help about Selenium is the [Official User Group](https://groups.google.com/forum/#!forum/selenium-users). Here, you'll find that most of the time, someone already found the problem you are facing right now, and usually reached the solution for which you are looking.

_Note: Please make sure to search the group before asking for something. Your question likely won't get answered if it was previously answered in another discussion!_

### Chat Room

The best place to ask for help is the user group (because they also keep the information accessible for others to read in the future). However, if you have a very important (or too simple) issue that needs a solution ASAP, you can always enter the IRC chat room. You might just find someone ready to help on `#selenium` at [Freenode](https://freenode.net/).

### Issues

If you have any problems with or questions about this image, please contact us through a [Github issue](https://github.com/SeleniumHQ/docker-selenium/issues). If you have any problems with or questions about Selenium, please contact us through Selenium's [Bug Tracker](https://code.google.com/p/selenium/issues/list).ems with or questions about Selenium, please contact us through Selenium's [But Tracker](https://code.google.com/p/selenium/issues/list).

## Contributing

There are many ways to [contribute](http://docs.seleniumhq.org/about/getting-involved.jsp) whether by answering user questions, additional docs, or pull request we look forward to hearing from you.

If you do supply a patch we will need you to [sign the CLA](https://spreadsheets.google.com/spreadsheet/viewform?hl=en_US&formkey=dFFjXzBzM1VwekFlOWFWMjFFRjJMRFE6MQ#gid=0). We are part of [SFC](http://www.sfconservancy.org/)
