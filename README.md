# Cloud_native_Monitoring
1. Using Python creating an Monitoring Application in Python using Flask and psutil
2. run  Python App locally.
3.  Docker and containerize the Python application
    1. Creating Dockerfile
    2. Building DockerImage
    3. Running Docker Container
    4. Docker Commands
4. Create ECR repository using Python Boto3 and pushing Docker Image to ECR
5. using Kubernetes and Create EKS cluster and Nodegroups
6. Create Kubernetes Deployments and Services using Python!
```
screenshots:

![image](https://github.com/Chitreshkpk/Cloud_native_Monitoring/assets/133502661/4f6da91f-3836-4431-97d7-339364d767f5)
![image](https://github.com/Chitreshkpk/Cloud_native_Monitoring/assets/133502661/fb19dddc-e12e-48f3-94b8-f44e8b2a0420)


Step 1: Create a Dockerfile**

Create a **`Dockerfile`** in the root directory of the project with the following contents:

```
# Use the official Python image as the base image
FROM python:3.9-slim-buster

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file to the working directory
COPY requirements.txt .

RUN pip3 install --no-cache-dir -r requirements.txt

# Copy the application code to the working directory
COPY . .

# Set the environment variables for the Flask app
ENV FLASK_RUN_HOST=0.0.0.0

# Expose the port on which the Flask app will run
EXPOSE 5000

# Start the Flask app when the container is run
CMD ["flask", "run"]
```

### **Step 2: Build the Docker image**

To build the Docker image, execute the following command:

```
$ docker build -t <image_name> .
```

### **Step 3: Run the Docker container**

To run the Docker container, execute the following command:

```
$ docker run -p 5000:5000 <image_name>
