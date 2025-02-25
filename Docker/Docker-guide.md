# Learning how to use Docker.

## Overview
In this guide, you will be able to do the following:

- Create a simple **Flask application**
- Create a **Dockerfile** to containerise the application
- Build the Docker image from the **Dockerfile** and run it locally in order to access application from the browser.
- Write a `docker-compose.yml` file to run a multi-container application(web app & mysql database)
- Push the built image to Dockerhub

---


## 1: Install Docker and verify the installation by running	a	simple	container.
1. Go to the [Docker](https://www.docker.com/products/docker-desktop/) website and download the application. Select your working OS( Windows, MacOS or Linux).
2. Once the download is finished, go to your **terminal** and run `docker --version`. This will print out the version of Docker you're using. If you see the version number, that means Docker is installed.
3. On the **terminal**, run the following command:
```
docker run hello-world
```
You will see the message **"Unable to find image 'hello-world':latest locally"**. this means it could not find the image on your machine. This image will then be pulled from the **library** where it's stored, which is **DockerHub**.

Docker will then create a **container** from the image and runs it. Once you run the container, you will see the message "Hello from Docker". This shows the installation was a success. 


---


## 2: Create a simple Flask application using Python
**FLask** is a simple and lightweight framwork for creating web applications in **Python**. Go the [Python](https://www.python.org/) website and download the latest version for your OS( Windows, MacOS or Linux). Once done, use the following command to confirm the installation
```
python3 --version
```

Next, use the `pip` commmand in order to install **Flask** and all of its dependencies. Depending on the Python version you've downloaded, use the appropriate **number** after `pip`
```
pip3 install flask
```

This will install **Flask** and all of its dependencies. Now you are ready to build your web application.

Now you will create a **directory** on your command line and start working from that **directory**. Give the **directory** a suitable name. 
```
mkdir hello_flask
cd hello_flask
```

Next create your application file. Since you will be using **Python**, end the file name with `.py`
```
touch app.py
```

Input the following onto your `app.py` file
```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, world!'

if  __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```


`from flask import Flask`: This imports the Flask class from the Flask framework, allowing you to create a web application in Python.

`@app.route('/')` > Maps the root URL (/) to the function below.

`def hello_world():` > Defines a function that handles requests to /.

`return 'Hello, world!'`> Responds with "Hello, world!" when accessed.( You can change this to whatever you would like )

`if __name__ == '__main__':` > Ensures the script runs only when executed.

`app.run(host='0.0.0.0', port=5002)` > Starts the Flask server:
  - `host='0.0.0.0'` > Makes the app accessible on all network interfaces.
  - `port=5002` > Runs the app on port 5002.

Run the application on your machine to ensure its works as expected.
```
python3 app.py
```

The application will start running on localhost on `port 5002`: `127.0.0.1:5002`. Click on the link that appears on your **terminal** and it will take you to the website with your custom message displaying. 


<img width="456" alt="image" src="https://github.com/user-attachments/assets/fcacf3ed-acf6-4c48-89e2-09b1a82ed756" />

To stop the server from running, press `ctrl+C` on your keyboard.



## 3: Containerise your application using Docker
As you have created a web application, its time to containerise the app using Docker. After this step, you will have a Docker container running your **Python** app, allowing you to deploy it anywhere. 

Start by writing a **Dockerfile**.  A **DockerFile** is a text-file that provides step-by-step instructions on how to build a docker image. Create the **Dockerfile** in the `hello_flask` directory
```
touch Dockerfile
```

Note: Make sure you capitalise the first letter(D). Also, a Dockerfile does **not** have an extension.

Now it's time to start writing the contents of the **Dockerfile**.
```
FROM python:3.8-slim

WORKDIR /app

RUN pip install flask 

COPY . .

EXPOSE 5002

CMD ["python", "app.py"]
```

`FROM python:3.8-slim` > Uses a lightweight Python 3.8 image as the base.

`WORKDIR /app` > Sets `/app` as the working directory inside the container.

`RUN pip install flask` > Installs Flask inside the container.

`COPY . .` > Copies all files from the current directory(`app.py`) to the container.

`EXPOSE 5002` > Ensures that the app will run on port 5002(This was set when creating the application.)

`CMD ["python", "app.py"]` > Runs `app.py` app using Python when the container starts.

├── hello-flask (directory)
│   ├── app.py
│   |── Dockerfile
├── |── docker-compose.yml

