# Google Cloud Fundamentals: Getting Started with App Engine#

## Overview

Create and deploy a simple App Engine application using a virtual environment in the Google Cloud Shell.

## Objectives

In this lab, the objectives are to perform the following tasks: - Initialize App Engine. - Preview an App Engine application running locally in Cloud Shell. - Deploy an App Engine application, so that others can reach it. - Disable an App Engine application, when you no longer want it to be visible.

## Task 1: Initialize App Engine

If you are accessing gcloud via your local machine's CLI:

- List all credentialed accounts.

  > gcloud auth list

  if no accounts are listed:

  > gcloud auth login

- To set the active account:
  > gcloud config set account `ACCOUNT`

### Steps:

#### 1. Initialize your App Engine app with your project and choose its region

        > gcloud app create --project=$DEVSHELL_PROJECT_ID

#### 2. Clone the source code repository for a sample application in the hello_world directory:

        > git clone https://github.com/GoogleCloudPlatform/python-docs-samples

#### 3. Navigate to the source directory:

        > cd python-docs-samples/appengine/standard_python3/hello_world

## Task 2: Run Hello World application locally

In this task, you run the Hello World application.

### Steps:

#### 1. Execute the following command to download and update the packages list:

        > sudo apt-get update

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
