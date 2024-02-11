# Image-Recognition-Using-AWS

## Overview

The **AWS Image Recognition as a Service** project aims to provide users with a cloud-based solution for image recognition. Leveraging Amazon Web Services (AWS) resources, this application performs deep learning on user-provided images. Key features include concurrent request handling, automatic scaling, and seamless integration with AWS services.

## Project Details

### 1. Objective

The primary goal of this project is to create a cloud app that offers image recognition capabilities. Users can submit images, and the system processes them using a pre-trained deep learning model hosted on AWS.

### 2. Components

#### Web-Tier-AWS

- A RESTful Web Service that accepts image requests (via Image URLs) and places them in an Input Queue.
- Monitors the Output Queue for classification results.
- Utilizes a load balancer to dynamically create app instances during high demand (scaling out).

#### Listener

- Runs within app instances and listens for messages in the Input Queue.
- Processes incoming messages by running the deep learning model for image classification.
- Stores classification results in an S3 bucket and inserts them into the Output Queue.
- Initiates instance shutdown when the Input Queue is empty (scaling in).

#### Listener Running

- Similar to the Listener application but ensures that the instance running this application remains active for quick responses.

### 3. AWS Services Used

- **Elastic Compute Cloud (EC2):** Provides scalable compute resources for running app instances.
- **Simple Queue Service (SQS):** Manages message queues for communication between components.
- **Simple Storage Service (S3):** Stores classification results and other data.

## Getting Started

1. Clone this repository: https://github.com/SarvaniDesu/Image-Recognition-Using-AWS.git

2. Install dependencies and configure your AWS credentials.

3. Set up the deep learning model (AMI ID: ami-07303b67, Name: imageRecognition, Region: us-west-1a).

4. Update relevant configuration files (e.g., connection strings, queue names).

5. Deploy the application and start processing image requests.
