# Lab2: CRUD Operations with Python & Flask

## Description

In this lab, I created a product list using a Flask server. The application allows you to add a product, retrieve all products, retrieve a specific product by its ID, update a specific product by its ID, and delete a product by its ID. All these operations are achieved through REST API endpoints in the Flask server.

I used cURL and POSTMAN to test the implemented endpoints.

## Learning Objectives

After completing this lab, I am able to:
- Create API endpoints to perform Create, Retrieve, Update, and Delete operations on transient data with a Flask server.
- Create REST API endpoints and use POSTMAN to test the REST APIs.

## Steps to Complete the Lab

### Step 1: Set Up the Application

1. **Open a Terminal Window:**
   - Use the menu in the editor: `Terminal > New Terminal`.

2. **Change to Your Project Folder:**
   - Run the following command to navigate to the project folder:
     ```sh
     cd /home/project
     ```

3. **Clone the Git Repository:**
   - If the repository doesn't already exist, run the following command to clone it:
     ```sh
     [ ! -d 'jmgdo-microservices' ] && git clone https://github.com/ibm-developer-skills-network/jmgdo-microservices.git
     ```

4. **Change to the CRUD Directory:**
   - Run the following command to navigate to the CRUD directory:
     ```sh
     cd jmgdo-microservices/CRUD
     ```

5. **List the Contents of the Directory:**
   - Run the following command to see the artifacts for this lab:
     ```sh
     ls
     ```

6. **Install Required Packages:**
   - Run the following command in the terminal to install the necessary packages:
     ```sh
     python3 -m pip install flask flask_cors
     ```

### Step 2: Understand the Server Application

1. **Open `products.py` in the IDE:**
   - Navigate to the `jmgdo-microservices/CRUD` folder in the Files Explorer and open `products.py`.

2. **Import Required Packages:**
   - Add the following code at the beginning of `products.py`:
     ```python
     from flask import Flask, jsonify, request
     import json
     ```

3. **Create the Flask Application:**
   - Add the following code to create the Flask application:
     ```python
     app = Flask("Product Server")
     ```

4. **Precreated Products:**
   - Define the precreated products in the following code:
     ```python
     products = [
         {'id': 143, 'name': 'Notebook', 'price': 5.49},
         {'id': 144, 'name': 'Black Marker', 'price': 1.99}
     ]
     ```

5. **Create REST API Endpoints:**
   - Add the following code to define the REST API endpoints for CRUD operations:
     ```python
     @app.route('/products', methods=['GET'])
     def get_products():
         return jsonify(products)

     @app.route('/products/<id>', methods=['GET'])
     def get_product(id):
         id = int(id)
         product = [x for x in products if x["id"] == id][0]
         return jsonify(product)

     @app.route('/products', methods=['POST'])
     def add_product():
         products.append(request.get_json())
         return '', 201

     @app.route('/products/<id>', methods=['PUT'])
     def update_product(id):
         id = int(id)
         updated_product = json.loads(request.data)
         product = [x for x in products if x["id"] == id][0]
         for key, value in updated_product.items():
             product[key] = value
         return '', 204

     @app.route('/products/<id>', methods=['DELETE'])
     def remove_product(id):
         id = int(id)
         product = [x for x in products if x["id"] == id][0]
         products.remove(product)
         return '', 204
     ```

### Step 3: Run and Test the Server with cURL

1. **Run the Python Server:**
   - Start the Python server using the following command:
     ```sh
     python3 products.py
     ```

2. **Open Another Terminal:**
   - Open another terminal by clicking the `Terminal` menu and selecting `New Terminal`.

3. **Access the API Endpoint:**
   - Run the following command to access the `http://localhost:5000/products` API endpoint:
     ```sh
     curl http://localhost:5000/products
     ```

4. **Add a Product:**
   - Run the following command to add a product to the list:
     ```sh
     curl -X POST -H "Content-Type: application/json" \
     -d '{"id": 145, "name": "Pen", "price": 2.5}' \
     http://localhost:5000/products
     ```

5. **Verify if the Product is Added:**
   - Run the following command to verify if the product has been added:
     ```sh
     curl http://localhost:5000/products/145
     ```

### Step 4: Test the REST API Endpoints with POSTMAN

1. **Sign Up for Postman:**
   - Go to [Postman](https://www.postman.com/) and sign up for an account.

2. **Create a New Request:**
   - Click `Create New` and choose `HTTP Request`.

3. **Enter the URL and Select the Request Type:**
   - Paste the server URL into the address bar and change the request type to `POST`.
   - Choose `raw -> body -> JSON` to send input as JSON.

4. **Add a Product (POST Request):**
   - Enter the following JSON object in the body and click `Send`:
     ```json
     {
         "id":146,
         "name":"Laptop Bag",
         "price":45.00
     }
     ```

5. **Verify Added Products:**
   - Change the request type to `GET` and remove the JSON object from the request body.
   - Click `Send` and observe the output to ensure that the product has been added.

6. **Update Product Details (PUT Request):**
   - Change the price of the item with id `146` to `42.00`.
   - Set the request type to `PUT` and add the product id to the end of the URL.
   - Add the value to be changed as a JSON body:
     ```json
     {
         "price":42.00
     }
     ```
   - Click `Send`.

7. **Verify Updated Product:**
   - Change the request type to `GET` and remove the JSON object from the request body.
   - Click `Send` and observe the output to ensure that the product is updated.

### Practice Labs

1. **Update Product Details of Product with id 144:**
   - Change its price to `2.50` using a `PUT` request.

2. **Add a Product using POST Method:**
   - Add the following product:
     ```json
     {
         "id":142,
         "name":"Eraser",
         "price":1.50
     }
     ```

3. **Delete the Product with id 142:**
   - Use a `DELETE` request to remove the product.


