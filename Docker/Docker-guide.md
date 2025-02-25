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

Finally, create a **Git** repo

---


## 2: Create a simple Flask application using Python
**FLask** is a simple and lightweight framwork for creating web applications in **Python**. Go the [Python](https://www.python.org/) website and download the latest version for your OS( Windows, MacOS or Linux). Once done, use the following command to confirm the installation
```
python3 --version
```

Next, use the `pip` commmand in order to install **Flask** and all of its dependencies.Depending on the Python version you've downloaded, use the appropriate **number** after `pip`
```
pip3 install flask
```

This will install **Flask** and all of its dependencies. Now you are ready to build your web application.

Now you will create a **directory** on your command line and start working from that **directory**. Give the **directory** a suitable name. 
```
mkdir hello_flask
cd hello_flask
```



## 3: Create a Dockerfile
A DockerFile provides a step-by-step instructions on how to build a docker image.is a You will need to first create a simple web application in order to containerise using **Dockerfile**. 



├── hello-flask (directory)
│   ├── app.py
│   |── Dockerfile
├── |── docker-compose.yml

