# Google Cloud Fundamentals: Getting Started with Compute Engine

## Overview

In this lab, you will create virtual machines (VMs) and connect to them. You will also create connections between the instances.

## Objectives

In this lab, the objectives are to perform the following tasks:
    - Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

    - Create a Compute Engine virtual machine using the gcloud command-line interface.

    - Connect between the two instances.

## Task 1: Sign in to GCP

If you are accessing gcloud via your local machine's CLI:

- List all credentialed accounts.

  > gcloud auth list

  if no accounts are listed:

  > gcloud auth login

- To set the active account:
  > gcloud config set account `ACCOUNT`



## Task 2: Create a virtual machine using the GCP Console

        > gcloud compute instances create vm-1 -- machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9

#### 2. Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system:

        > sudo apt-get install virtualenv

        If prompted [Y/n], press Y and then Enter.

        > virtualenv -p python3 venv

#### 3. Activate the virtual environment:

        > source venv/bin/activate

#### 4. Navigate to your project directory and install dependencies:

        > pip install  -r requirements.txt --project=$DEVSHELL_PROJECT_ID

#### 5. Run the application:

        > python main.py

## Task 3: Deploy and run Hello World on App Engine

In this task, you run the Hello World application.

### Steps:

#### 1. Navigate to the source directory:

        > cd ~/python-docs-samples/appengine/standard_python3/hello_world

#### 2. Deploy your Hello World application:

        > gcloud app deploy

        If prompted [Y/n], press Y and then Enter.

#### 3. Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com:

        > gcloud app browse

        Ctrl+click to open the URL a browser window, you should see `Hello World`.

## Task 4: Deploy and run Hello World on App Engine

App Engine offers no option to Undeploy an application. After an application is deployed, it remains deployed, although you could instead replace the application with a simple page that says something like "not in service."

However, you can disable the application, which causes it to no longer be accessible to users.

    > gcloud app versions list --filter=hello_world DISABLE
