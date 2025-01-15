# Lab1: Creating a HELLO WORLD REST API with Python & Flask

## Description

In this lab, I created my first REST API Hello World application using Flask. Flask is a lightweight WSGI web application framework in Python. It's designed with simplicity in mind, making it easy to create simple web applications quickly.

## Learning Objectives

After completing this lab:
- I am able to create a simple web application using Flask.
- I am able to access the REST API endpoints of my application through the browser.

## Steps to Complete the Lab

### Step 1: Set Up a Flask Server

1. **Open a new Terminal in the lab environment:**
   - Open a new terminal using the menu: `Terminal > New Terminal`.

2. **Create a Python file:**
   - Run the following command to create a file named `server.py`:
     ```sh
     touch /home/project/server.py
     ```

3. **Open `server.py` in the IDE:**
   - Navigate to the file in your IDE to open it.

4. **Paste the following code into `server.py` and save the file:**
   ```python
   from flask import Flask
   app = Flask("My Hello World Application")

   @app.route("/")
   def hello():
       return "Hello World!"

   if __name__ == "__main__":
       app.run(debug=True)
   # When no port is specified, starts at default port 5000
   ```

5. **Install Flask Package:**
 ``` 
python3 -m pip install flask 
```

6. **Run the Flask Application:** 
```
python3 server.py
```

7. **Access the REST API Endpoint:** 
```
http://localhost:5000
```