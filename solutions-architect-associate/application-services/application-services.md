# Application Services
* Step Functions
* **SWF**
* API Gateway
* Elastic Transcoder


# Step Functions
*


# Simple Workflow (SWF)
* Managed State Tracker and Task Coordinator
* Devs build background jobs with parallel or sequential steps

### General
* A way to coordinate tasks across distributed application components.
* SQS has a retention period of *14 days*, SWF up to *1 year* for workflow executions.
* Amazon SWF presents a *task-oriented API*, whereas Amazon SQS offers a *message-oriented API*.
* Amazon SWF ensures that a task is assigned **only once** and is never duplicated. With Amazon SQS, you need to handle duplicated messages and may also need to ensure that a message is processed only once.
* Amazon SWF keeps track of all the tasks and events in an application.  With Amazon SQS, you need to implement your own application-level tracking, especially if your application uses multiple queues.

### SWF Actors
* **Workflow Starters** - an application that can initiate a workflow
* **Deciders** - control the flow of activity tasks in a workflow execution
* **Activity Workers** - Carry out the activity tasks
  * Can be humans *(not specific to AWS resources)*

### Benefits
* HA
* Separate state and work
* Supports human worker tasks

### Components
* Task
* Marker
* Timer
* Signal


# API Gateway
* Create, publish, maintain, monitor, secure APIs

### API Gateway Control Service
* Create Restful API for backend services

### API Gateway Execution Service
*

### Alternatives
* Nginx
* Zuul
* Apigee
* Kong


# Elastic Transcoder
* Transcode media files from source format into versions that will playback on devices like smartphones, tablets, and PCs.
* **Progressive download** or adaptive bitrate **streaming** (HLS, Smooth, or MPEG-DASH) with CloudFront
