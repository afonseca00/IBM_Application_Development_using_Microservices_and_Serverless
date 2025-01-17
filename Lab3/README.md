# Lab3: Creating Swagger Documentation for REST API

## Description

In this lab, I learned how to create Swagger documentation for REST APIs. Swagger is an open-source tool that helps design, build, document, and consume REST APIs. This lab covers using the Swagger Editor to create documentation, accessing REST API endpoints using SwaggerUI, and generating server code with Swagger documentation.

## Learning Objectives

After completing this lab, I am able to:
- Use the Swagger Editor to create Swagger documentation for REST APIs.
- Use SwaggerUI to access REST API endpoints of an application.
- Generate server code with Swagger documentation.


## Pre-requisites

- Familiarity with Docker applications and commands.
- A good understanding of REST APIs.
- Knowledge of Python is highly recommended.

## Steps to Complete the Lab

### Task 1: Getting Your Application Started

1. **Open a Terminal Window:**
   - Use the top menu in the IDE: `Terminal > New Terminal` if you don’t have one open already.

2. **Clone the Repository:**
   - In the terminal, clone the repository which has the Swagger documentation and the REST API code ready by running the following command:
     ```sh
     git clone https://github.com/ibm-developer-skills-network/jmgdo-microservices.git
     ```

3. **Change the Working Directory:**
   - Change the working directory to `jmgdo-microservices/swagger_example` by running the following command:
     ```sh
     cd jmgdo-microservices/swagger_example
     ```

4. **Install Required Packages:**
   - Run the following command to install the required packages:
     ```sh
     python3 -m pip install flask_cors
     ```

### Task 2: Creating Swagger Documentation

1. **Define Your Application in Swagger Editor:**
   - It will adhere to Swagger 2.0 version.
   - This is the first version of the application.
   - It will have one endpoint `/greetings`, which returns the list of greetings as a JSON object.

2. **Copy and Paste JSON in Swagger Editor:**
   - Copy the following JSON and paste it into the Swagger Editor:
     ```json
     {
         "swagger": "2.0",
         "info": {
           "version": "1.0",
           "title": "Our first generated REST API",
           "description": "<h2>This is a sample server code that is generated from Swagger Documentation with Swagger Editor</h2>"
         },
         "paths": {
           "/greetings": {
             "get": {
               "summary": "Returns a list of Greetings",
               "tags": ["Hello in Different Languages"],
               "description": "Returns greetings in different languages",
               "produces": [
                 "application/json"
               ],
               "responses": {
                 "200": {
                   "description": "OK"
                 }
               }
             }
           }
         }
     }
     ```
   - You will get a prompt which says "Would you like to convert your JSON into YAML?". Press **Cancel** to paste the content as JSON.

3. **View Swagger UI:**
   - You will see the Swagger UI automatically appear on the right. You cannot test it yet as your application is not defined and running yet.

4. **Generate Server Code:**
   - From the menu on top, click on **Generate Server** and select `python-flask`.
   - This will automatically generate the server code as a zip file named `python-flask-server-generated.zip`.
   - Download the zip file to your system.

### Task 3: Setting Up the Server

1. **Upload and Extract the Zip File:**
   - In your lab environment, click on the **PROJECT** folder and drag and drop the zip file there.
   - On the terminal, navigate to the `/home/project` directory:
     ```sh
     cd /home/project
     ```
   - Unzip the contents of the zip file into a directory named `python-flask-server-generated` by running the following command:
     ```sh
     unzip python-flask-server-generated.zip -d python-flask-server-generated/
     ```

2. **Change to the Extracted Folder:**
   - Change to the `python-flask-server` folder inside the folder you just extracted the zip file into:
     ```sh
     cd python-flask-server-generated/python-flask-server
     ```

### Task 4: Building and Running the Server

1. **Build the Docker Image:**
   - Run the following command to build the server code:
     ```sh
     sudo docker build . -t mynewserver
     ```

2. **Run the Docker Application:**
   - Execute the following command to run the Docker application. The server-generated code is configured to run on port 8080:
     ```sh
     sudo docker run -dp 8080:8080 mynewserver
     ```

3. **Confirm the Service is Running:**
   - Execute the following command to confirm that the service is running and your REST API works:
     ```sh
     curl localhost:8080/greetings
     ```

### Task 5: Updating the API Response

1. **Stop the Running Server:**
   - Get the Docker container ID by running the following command and copying the container ID:
     ```sh
     docker ps | grep mynewserver
     ```
   - Stop the container using the following command, replacing `<container_id>` with the actual container ID you copied:
     ```sh
     docker kill <container_id>
     ```

2. **Update the REST API Response:**
   - In the file explorer, navigate to `python-flask-server-generated/python-flask-server/swagger_server/controllers/hello_in_different_languages_controller.py`.
   - Replace the line `return 'do some magic!'` with the following code:
     ```python
     def greetings_get():  # noqa: E501
         """Returns a list of Greetings

         Returns greetings in different languages # noqa: E501


         :rtype: None
         """
         hellos = {
             "English": "hello",
             "Hindi": "namastey",
             "Spanish": "hola",
             "French": "bonjour",
             "German": "guten tag",
             "Italian": "salve",
             "Chinese": "nǐn hǎo",
             "Portuguese": "olá",
             "Arabic": "asalaam alaikum",
             "Japanese": "konnichiwa",
             "Korean": "anyoung haseyo",
             "Russian": "Zdravstvuyte"
         }
         return hellos
     ```

3. **Build the Docker Container Again:**
   - Build the Docker container to incorporate the changes:
     ```sh
     sudo docker build . -t mynewserver
     ```

4. **Run the Docker Container:**
   - Run the container with the following command. Using `-p` instead of `-dp` ensures that the server is not running in the background, allowing you to see any errors if they occur:
     ```sh
     sudo docker run -p 8080:8080 mynewserver
     ```

5. **Access the Application:**
   - Click on the **Skills Network** button on the left to open the "Skills Network Toolbox".
   - Click **Launch Application**, enter the port number as `8080`, and click **Your Application**. This will open a browser window.
   - Append the path `/greetings` to the URL in the browser. You should see the greetings displayed on the page.


