# Final Project: Microservices Based Serverless Application

## Description

In this final project, I deployed multiple microservices to create an integrated application. These components consist of two backend microservices, one developed in Python and the other in Node.js, complemented by a front-end microservice.

## Objectives

After completing this project, I was able to:
- Create an application consisting of multiple microservices.
- Deploy Python and Node.js microservices on IBM Cloud Code Engine.
- Deploy the frontend microservice on IBM Cloud Code Engine.

## Part A: Deploying the Backend Microservices

### 1. Deploy the Microservice for Product Details (Python)

1. **Open the Code Engine CLI.**
2. **Deployed the Product Details microservice using the following command:**
    ```sh
    ibmcloud ce application create --name prodlist --image us.icr.io/${SN_ICR_NAMESPACE}/prodlist --registry-secret icr-secret --port 5000 --build-context-dir products_list --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
    ```
3. **Copied the deployment URL and saved it in a notepad.**
4. **Took a screenshot of the successful deployment and saved it as `product_details_deploy.png`.**

### 2. Deploy the Microservice for Dealer Pricing (Node.js)

1. **Deployed the Dealer Pricing microservice using the following command:**
    ```sh
    ibmcloud ce application create --name dealerdetails --image us.icr.io/${SN_ICR_NAMESPACE}/dealerdetails --registry-secret icr-secret --port 8080 --build-context-dir dealer_details --build-source https://github.com/ibm-developer-skills-network/dealer_evaluation_backend.git
    ```
2. **Copied the deployment URL and saved it in a notepad.**
3. **Took a screenshot of the successful deployment and saved it as `dealer_details_deploy.png`.**

## Part B: Deploying the Frontend Microservice

### 1. Clone the Frontend Repository

1. **In the terminal, went to the `/home/project` directory:**
    ```sh
    cd /home/project
    ```
2. **Cloned the repository using the following command:**
    ```sh
    git clone https://github.com/ibm-developer-skills-network/dealer_evaluation_frontend.git
    ```
3. **Took a screenshot of the successful git cloning and saved it as `git_clone.png`.**

### 2. Update the `index.html` File

1. **Changed to the `dealer_evaluation_frontend` directory:**
    ```sh
    cd dealer_evaluation_frontend
    ```
2. **Opened the `index.html` file and updated it with the deployment URLs obtained from the microservice deployments. Ensured the URLs ended with `/`.**
3. **Took a screenshot of the changes and saved it as `index_urlchanges.png`.**

### 3. Deploy the Dealer Evaluation Frontend Microservice

1. **Deployed the frontend microservice using the following command:**
    ```sh
    ibmcloud ce application create --name frontend --image us.icr.io/${SN_ICR_NAMESPACE}/frontend --registry-secret icr-secret --port 5001 --build-source .
    ```
2. **Took a screenshot of the successful deployment and saved it as `frontend_deploy.png`.**

**Note:** If I encountered the error `FAILED Wait failed for application 'frontend'`, I could rename the application to `frontend1` and re-execute the command.

## Verification

### 1. Open the Deployment Link

1. **Clicked the link to load the homepage. Noted that the page might take time to load the first time I accessed it.**
2. **Clicked the products dropdown to see if the products were populated.**
3. **Took a screenshot of the homepage showing the products list and saved it as `homepage.png`.**

### 2. Verify Dealer Pricing

1. **Chose a specific dealer for the product and verified the price was displayed.**
2. **Took a screenshot of the entire page showing the product chosen and dealers supplying the product listed by the microservice and saved it as `product_dealer.png`.**

### 3. Verify Dealer Pricing for a Specific Dealer

1. **After the dealers dropdown was populated, chose a specific dealer for the product and checked if the price charged by that dealer was displayed.**
2. **Allowed 10 to 20 seconds for the page to load.**
3. **Took a screenshot of the entire page showing the product chosen, dealer chosen, and the price returned by the microservice and saved it as `product_dealer_price.png`.**

### 4. Verify Pricing for All Dealers

1. **Chose the "All Dealers" option for a product (ensured to choose a product which had more than one dealer). The pricing of all dealers offering the product was shown on the screen.**
2. **Took a screenshot of the entire page showing the product chosen, the "All Dealers" option chosen, and the prices charged by all dealers returned by the microservice and saved it as `product_all_dealers_prices.png`.**


