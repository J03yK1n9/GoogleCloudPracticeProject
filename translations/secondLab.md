# Google Cloud Fundamentals: Getting Started with Compute Engine

## Overview

In this lab, you will create virtual machines (VMs) and connect to them. You will also create connections between the instances.

## Objectives

In this lab, the objectives are to perform the following tasks: - Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

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

## Task 2:

    - Steps:
     1. Create a virtual machine

        > gcloud compute instances create vm-1 -- machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v28190213" --subnet "default" --tags http

        > gcloud compute firewall-rules create allow-http --action=ALLOW --direction=INGRESS --rules=tcp:80 --target-tags=http

     2.

        > gcloud config set copmute/zone us-central-b

        > gcloud compute instances create vm-2 -- machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v28190213" --subnet "default"

     3. Connect between the two instances.

        1. Use the ping command to  confirm that vm-2 can reach vm-1 over the network:
            - Connect vm-2:
             > gcloud compute ssh my-vm-2

            - ping vm-1 from vm-2:
             > ping -c 4 vm-1

            - Use the ssh command to open a command prompt on vm-1 from vm-2:
             > ssh vm-1

            - At the command prompt on vm-1, install the Nginx web sever:
             > sudo apt-get install nginx-light -y

            - Use nano text editor to add a custom message to the default home page of the web server:
             > sudo nano /var/www/html/index/nginx-debian.html

            - Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name:
             > Hi from YOUR_NAME

            - Exit the editor:
               Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.

            - Confirm that the web server is serving your new page, at the command prompt on vm-1
             > curl http://localhost/
             The response will be the HTML source of the web server's home page, including your line of custom text.

            - Exit cmd:
             > exit

            - Confirm that vm-2 can reach web server on vm-1 at the cmd on vm-2:
             > curl http://my-vm-1/
             The response will again be the HTML source of the web server's home page, including your line of custom text.

     4. Get the external IP of the vm-1 instance:
      > gcloud compute instances list --zone us-central-a

     5. Paste it into the address bar of a new browser tab and press enter.
        the result should be your web server's home page, including your custom text
