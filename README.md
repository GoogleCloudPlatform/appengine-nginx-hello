![status: inactive](https://img.shields.io/badge/status-inactive-red.svg)

This project is no longer actively developed or maintained.  

For more information about App Engine, refer to our [documentation](https://cloud.google.com/appengine).

Getting Started
===============

If you haven't already, make sure you are familiar with Custom Runtimes in the
[App Engine Managed VM documentation](https://cloud.google.com/appengine/docs/managed-vms/custom-runtimes).

You must have the [Google Cloud SDK](https://cloud.google.com/sdk/), with the [Managed VM component](https://cloud.google.com/appengine/docs/managed-vms/) installed.
We will assume that the SDK is available on your command line as `$ gcloud`.

You must also [install
Docker](https://docs.docker.com/installation/#installation) on your
workstation, as the SDK uses it to build, test and deploy your application.

What's in this Repository?
==========================

This is a minimal Managed VM runtime that runs the nginx server.  It
implements the two required handlers (`/_ah/start` and `/_ah/health`) as
static pages and illustrates the files necessary to run a custom runtime.

+ `app.yaml` - Configuration file for App Engine.
+ `Dockerfile` - Defines your docker image.
+ `www/index.html` - Root page to be served by nginx.
+ `nginx.conf` - nginx configuration file.
+ `ok` - File content served by start and health handlers.

Running Locally
===============

First, make sure Docker has been started on your workstation. Refer to the
[Managed VM documentation](https://cloud.google.com/appengine/docs/java/managed-vms/)
for more information on how to do this for your environment.

Then, to run locally:

  `$ gcloud preview app run /path/to/appengine-nginx-hello`

This will build the nginx docker image and run it locally. You can access it
at [http://localhost:8080](http://localhost:8080).

Deploying your Application
==========================

To deploy to [App Engine](https://cloud.google.com/appengine/):

  `$ gcloud preview app deploy /path/to/appengine-nginx-hello`

This will build the nginx docker image and deploy it to App Engine.

Serving Static Files
====================

You can use this demo to serve static files from a managed vm. Just add files
to the www directory and they'll be added to the `/usr/share/nginx/www`
directory and served from your app.

License
=========

Copyright 2014 Google Inc.

[Licensed under the Apache License, version 2.0](LICENSE)
