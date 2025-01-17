# Lab5: Deploying My First Docker Image on Code Engine

## Description

In this lab, I learned how to deploy a "Hello World" web application from GitHub on IBM Cloud Code Engine. IBM Cloud Code Engine has been made available to me through this lab environment.

## Learning Objectives

After completing this lab, I was able to:
- Start the Code Engine service to create applications.
- Use the Code Engine service to deploy an application from a Docker image and create a remote access URL for the application.
- List the applications I have deployed.

## Pre-requisites

- Familiarity with Docker applications and commands.
- A basic understanding of cloud services and deployment.
- Access to IBM Cloud and IBM Cloud Code Engine CLI.

## Steps to Complete the Lab

### Task 1: Set Up Code Engine CLI

1. **Set Up Code Engine CLI:**
   - If you don’t have the Code Engine CLI set up, follow [this guide](https://cloud.ibm.com/docs/codeengine?topic=codeengine-getting-started-cli) to set it up.

### Task 2: Deploy the Docker Image

1. **List Existing Applications:**
   - I ran the following command to see the list of applications that exist:
     ```sh
     ibmcloud ce app list
     ```

2. **Clone the GitHub Repository:**
   - I cloned the code from GitHub using the following command:
     ```sh
     git clone https://github.com/ibm-developer-skills-network/danum-pythonflaskserver
     ```

3. **Navigate to the Cloned Directory:**
   - I changed to the cloned directory by running the following command:
     ```sh
     cd danum-pythonflaskserver
     ```

4. **Build the Docker Image:**
   - I built the Docker image and tagged it by running:
     ```sh
     docker build . -t us.icr.io/${SN_ICR_NAMESPACE}/helloworld2
     ```

5. **Push the Docker Image:**
   - I pushed the image to the namespace so that I could run it:
     ```sh
     docker push us.icr.io/${SN_ICR_NAMESPACE}/helloworld2
     ```

6. **Create the Application:**
   - I created the application by running the following command. This command sets up the required infrastructure and provides confirmation along with the URL:
     ```sh
     ibmcloud ce application create --name helloworld2 --image us.icr.io/${SN_ICR_NAMESPACE}/helloworld2 --registry-secret icr-secret --port 5000
     ```

### Task 3: Access the Application

1. **Access the Application:**
   - I pressed Ctrl (Windows)/Cmd (Mac) and clicked the link that was created. Alternatively, I copied the link and pasted it in a browser to access the "Hello World" application page.

### Practice Exercise

1. **Update the Application:**
   - I went to the file menu, opened `danum-pythonflaskserver/app.py` and changed the message from "Hello World" to "Hello yourname!".
   - I saved the file, built the Docker image again, and updated the application using the following command:
     ```sh
     ibmcloud ce application update --name helloworld2 --image us.icr.io/${SN_ICR_NAMESPACE}/helloworld2 --registry-secret icr-secret --port 5000
     ```

2. **Verify the Update:**
   - I opened the URL that was generated and confirmed that the application had been updated.


