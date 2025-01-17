# Lab6: Deploy, Update, and Scale Microservices using Serverless

## Description

In this lab, I learned how to create a UK University information application composed of two microservices on IBM Cloud Code Engine, and how to scale and update each microservice independently of the other. IBM Cloud Code Engine was made available to me through this lab environment.

## Learning Objectives

After completing this lab, I was able to:
- Start Code Engine service to create an application.
- Use the Code Engine service to deploy two microservices that are part of an application.
- Scale one of the microservices to have more than one instance.
- Update one of the microservices without having to stop and redeploy it.

## Pre-requisites

- Familiarity with Docker applications and commands.
- A basic understanding of microservices and serverless architecture.
- Access to IBM Cloud and IBM Cloud Code Engine CLI.

## Steps to Complete the Lab

### Task 1: Set Up Code Engine CLI

1. **Set Up Code Engine CLI:**
   - If you don’t have the Code Engine CLI set up, follow [this guide](https://cloud.ibm.com/docs/codeengine?topic=codeengine-getting-started-cli) to set it up.

### Task 2: Deploy the Microservices

1. **Clone the Repository:**
   - I cloned the repository using the following command:
     ```sh
     git clone https://github.com/ibm-developer-skills-network/gentu-microservices_practiceProj.git
     ```

2. **Navigate to the `universities` Directory:**
   - I changed to the `universities` directory by running:
     ```sh
     cd gentu-microservices_practiceProj/universities
     ```

3. **List the Directories:**
   - I listed the directories inside `universities` to see the microservices that I would deploy:
     ```sh
     ls
     ```
   - I saw two directories listed: `listing` and `websites`.

4. **Deploy the `listing` Microservice:**
   - I deployed the `listing` microservice using the following command:
     ```sh
     ibmcloud ce app create --name listing --image us.icr.io/${SN_ICR_NAMESPACE}/listing --registry-secret icr-secret --port 5000 --build-context-dir listing --build-source .
     ```

5. **Get the Details of the `listing` Application:**
   - I retrieved the details and URL of the `listing` application:
     ```sh
     ibmcloud ce app get -n listing
     ```

6. **Access the `listing` Endpoint:**
   - I accessed the endpoint to fetch all colleges with "Trinity" in their name:
     ```sh
     curl <your_deployment_url>/colleges/Trinity
     ```

7. **Deploy the `websites` Microservice:**
   - I deployed the `websites` microservice using the following command:
     ```sh
     ibmcloud ce app create --name websites --image us.icr.io/${SN_ICR_NAMESPACE}/websites --registry-secret icr-secret --port 5000 --build-context-dir websites --build-source .
     ```

8. **Access the `websites` Endpoint:**
   - I accessed the endpoint to fetch all websites for "Trinity College of Music":
     ```sh
     curl <your_deployment_url>/websites/Trinity%20College%20of%20Music
     ```

### Task 3: Scale the Microservices

1. **Scale the `listing` Microservice:**
   - I scaled the `listing` application to have a minimum of 2 instances:
     ```sh
     ibmcloud ce app update --name listing --min 2
     ```

2. **Verify Scaling:**
   - I verified that the `listing` application had scaled:
     ```sh
     ibmcloud ce app get --name listing -q
     ```

### Task 4: Update the Microservices

1. **Update the `websites` Microservice:**
   - I updated the `websites` microservice to enable keyword searches for websites by modifying `app.py` with the following code:
     ```python
     from flask import Flask
     from flask_cors import CORS
     import json
     app = Flask("University Websites")
     CORS(app)
     with open("UK_Universities.json", "r") as unifile:
         data = json.load(unifile)
     @app.route("/websites/<name>")
     def getCollegesWebsites(name):
         webpages = []
         for college in data:
             if college["name"].__contains__(name):
                 for website in college["web_pages"]:
                     webpages.append(website)
         return json.dumps({"Webpages": webpages}, indent=4)
     if __name__ == "__main__":
         app.run(debug=True, port=5000)
     ```

2. **Update the Application:**
   - I ran the following command to update the `websites` application:
     ```sh
     ibmcloud ce app update --name websites --image us.icr.io/${SN_ICR_NAMESPACE}/websites --registry-secret icr-secret --port 5000 --build-context-dir websites --build-source .
     ```

3. **Verify the Update:**
   - I verified the update by running:
     ```sh
     curl <your_deployment_url>/websites/Trinity
     ```

### Practice Exercise

1. **Scale the `websites` Microservice:**
   - I scaled the `websites` microservice to have 5 minimum instances.

2. **Update the `listing` Microservice:**
   - I updated the `listing` microservice to retrieve the list of universities in a case-insensitive manner and verified it by passing “TriniTY” as a parameter.

