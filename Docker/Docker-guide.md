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



## 3: Build the Docker image and containerise your application using Docker
As you have created a web application, its time to containerise the app using Docker. After this step, you will have a Docker container running your **Python** app, allowing you to deploy it anywhere. 

1. Start by writing a **Dockerfile**.  A **DockerFile** is a text-file that provides step-by-step instructions on how to build a docker image. Create the **Dockerfile** in the `hello_flask` directory
```
touch Dockerfile
```

**Note**: Make sure you capitalise the first letter(D). Also, a Dockerfile does **not** have an extension.

2. Now it's time to start writing the contents of the **Dockerfile**.
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

**Note**: Ensure that both files (app.py and Dockerfile) are placed within the `hello_flask` directory.

3. To build the Docker image, go back to your terminal and type in the following:
   ```
   docker build -t hello-flask .
   ```

   `docker build` > Creates a Docker image from the Dockerfile.

   `-t hello-flask` → Tags the image with the name "hello-flask" for easy reference.

   `.`> Uses the Dockerfile in the current directory.

   Once you press **enter**, Docker will execute each intruction in the **Dockerfile**. Once the build is complete, you will be ready to run the image as a **container**.

  4. Run the Docker image as a container. This will return a container ID
     ```
     docker run -d -p 5002:5002 hello-flask
     ```
   `docker run -d` > Starts the container in the background (detached mode).

   `-p 5002:5002` > Maps port 5002 of the container to 5002 on the your machine.

   This will return a container ID. This will indicate that your container is running. You can verify this by using the `docker ps` command. This will return the first 12 characters of the container ID, as well as the image name, the time 
   it was created etc. 

 5. Refresh the browser you were running your application on earlier(127.0.0.1:5002). This should display the previous webpage. This indicates that the application is running within the container you just created.
 
  
    To stop the container, you will need to use the `docker stop` command followed by the first 12 characters of container ID. Verify if the container has stopped running by using the `docker ps` command. 


---

## 4: Link Flask application to MySQL database container.

Start by modifying the `app.py` and `Dockerfile` to ensure that it installs the MySQL database.
```
# app.py

from flask import Flask
import MySQLdb

app = Flask(__name__)

@app.route('/')
def hello_world():
    # Connect to the MySQL database
    db = MySQLdb.connect(
        host="mydb",    # Hostname of the MySQL container
        user="root",    # Username to connect to MySQL
        passwd="my-secret-pw",  # Password for the MySQL user
        db="mysql"      # Name of the database to connect to
    )
    cur = db.cursor()
    cur.execute("SELECT VERSION()")
    version = cur.fetchone()
    return f'Hello, World! MySQL version: {version[0]}'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5002)
```

`import MySQLdb`: Imports the MySQLdb module, enabling Python to connect to and interact with a MySQL database.



```
## Dockerfile
FROM python:3.8-slim

WORKDIR /app

COPY . .

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config

RUN pip install flask mysqlclient

EXPOSE 5002

CMD ["python", "app.py"]
```

`pip install flask mysqlclient` > Installs Flask (a web framework) and mysqlclient (a MySQL database adapter for Python).

Create a custom network to allow the containers to communicate with each other.

Run the following command to create the network:
```
docker network create my-custom-network # Name of my network
```



Run the following command to run the MySQL container:
```
docker run -d --name mydb --network my-custom-network -e MYSQL_ROOT_PASSWORD=my-secret-pw mysql:8
```





`docker run -d` : Runs a container in detached mode (in the background).

`name mydb`: Assigns the name mydb to the container.

`network my-custom-network`: Connects the container to the custom Docker network named my-custom-network.

`-e MYSQL_ROOT_PASSWORD=my-secret-pw`: Sets the environment variable `MYSQL_ROOT_PASSWORD` inside the container to `my-secret-pw`, which is required to set the MySQL root password.

`mysql:8`: Specifies the Docker image and version to use for the container (mysql image, version 8).

---

### 4.1 Build the docker image for the Flask app using the updated Dockerfile.
```
docker build -t hello-flask-mysql .
```

Next, run the Flask application:
```
docker run -d --name myapp5 --network my-custom-network -p 5002:5002 hello-flask-mysql
```

### Output:
<img width="515" alt="image" src="https://github.com/user-attachments/assets/9a2fd31e-52c1-4e69-84ab-35acec7f34d6" />

Use `docker stop` to stop your containers.


---

## 5: Setup Docker Compose.
**Docker Compose** is a tool that allows you to define and manage multiple containers and Docker applications. It lets you define all your single files and manage them collectively. It offers an efficient way to manage multiple container Docker applications. 

First, create a `docker-compose.yml` file. This file lists all the services your application needs (like a blueprint that describes each container).
```
touch docker-compose.yml
```

Once the file is created, enter the following code:
```
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5002:5002"
    depends_on:
      - mydb

  mydb:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```

`version: '3.8'` > Specifies the version of the file-format. The lastest version is `3.8`.

`services`>  Defines the services (containers) in the app:

  - `.web:` > The Flask app container

   
- `.build: .` > Builds the Docker image from the current directory(`.`).
   
- `.ports: "5002:5002"`> Maps port 5002 on the host to port 5002 inside the container, allowing external access.

 - `depends_on: mydb` > Ensures the `mydb` service starts before web.


 `mydb` > The MySQL database container:

 - `image: mysql:8` > Uses the MySQL 8 image.
    
 - `environment:` > Sets environment variables for the container:

 -  `MYSQL_ROOT_PASSWORD: my-secret-pw` > Sets the MySQL root password.

---

### 5.1: Run  Docker Compose.
```
docker compose up -d
```

### Output:
<img width="1239" alt="image" src="https://github.com/user-attachments/assets/374cc7a4-a0b0-451b-ae94-c4147370295c" />


Take down the application using `docker compose down`. This will stop the containers.

---


## 6: Push to DockerHub.



├── hello-flask (directory)
│   ├── app.py
│   |── Dockerfile
├── |── docker-compose.yml

