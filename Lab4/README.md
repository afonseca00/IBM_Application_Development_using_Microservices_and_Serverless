# Lab4: Querying with GraphQL

## Description

In this lab, I learned how to use GraphQL to query APIs served through a GraphQL service running on a server using Postman. GraphQL is a query language for APIs and a runtime for executing those queries by providing a complete and understandable description of the data in an API.

## Learning Objectives

After completing this lab, I am able to:
- Use GraphQL with Postman to access a GraphQL Service.
- Structure queries to access APIs to get selective information that I need.


## Pre-requisites

- Familiarity with Docker applications and commands.
- A good understanding of APIs.
- Familiarity with using Postman.

## Steps to Complete the Lab

### Task 1: Sign-up for Postman

1. **Sign-up for Postman:**
   - If you already have a Postman account, you can skip this task.
   - On your browser, go to [Postman](https://www.postman.com/).
   - Click **Sign Up for Free**.
   - Enter your email, choose a password, confirm it, and create a free account. You can alternatively use your Google account to sign in too.
   - You have successfully created a Postman account.

### Task 2: Run a GraphQL Service

1. **Open a Terminal Window:**
   - Use the top menu in the IDE: `Terminal > New Terminal`.

2. **Clone the Repository:**
   - In the terminal, clone the repository which has the GraphQL service code ready by running the following command:
     ```sh
     git clone https://github.com/ibm-developer-skills-network/jmgdo-microservices.git
     ```

3. **Change the Working Directory:**
   - Change the working directory to `jmgdo-microservices/graphql_example` by running the following command:
     ```sh
     cd jmgdo-microservices/graphql_example
     ```

4. **Build the Application:**
   - Build the application by running the following command. This will build the Docker application using the Dockerfile in the current directory and tag it `graphqlservice`:
     ```sh
     docker build . -t graphqlservice
     ```

5. **Run the Application:**
   - Run the application that you just built on port 8080, by running the following command on the terminal:
     ```sh
     docker run -dp 8080:4000 graphqlservice
     ```

6. **Confirm the Service is Running:**
   - To confirm that the service is running, execute the following command:
     ```sh
     curl localhost:8080
     ```
   - If the output confirms that the service is up and running, proceed to the next steps.

7. **Launch the Application:**
   - Click on the **Skills Network** button on the left, it will open the "Skills Network Toolbox". Then click **Launch Application**, enter the port number as `8080`, and click **Your Application** button. This will open a browser window.
   - Copy the URL from the address bar.

### Task 3: Run GraphQL Queries on Postman

1. **Sign in to Postman:**
   - Go to [Postman](https://www.postman.com/) and sign in.

2. **Create a New Request:**
   - On the homepage, click **Create new**.
   - Choose **HttpRequest**.

3. **Enter the Request URL:**
   - In the space provided for the GET request URL, paste the URL you copied from the previous step and suffix it with `/graphql`.

4. **Choose Body and GraphQL:**
   - Choose **Body** and select **GraphQL** to start entering your query.

5. **Query for All US Cities:**
   - Paste the following in the Query tab and click **Send**:
     ```graphql
     {
         cities {
             city
             state
         }
     }
     ```

6. **Query for Florida Cities:**
   - To retrieve just the names of the cities in Florida, paste the following in the Query tab and click **Send**:
     ```graphql
     {
         cities(state: "Florida") {
             city
         }
     }
     ```

### Additional Task

1. **Query for Cities in Ohio:**
   - Construct a query to return all the cities in the state of "Ohio", along with the state name:
     ```graphql
     {
         cities(state: "Ohio") {
             city
             state
         }
     }
     ```


