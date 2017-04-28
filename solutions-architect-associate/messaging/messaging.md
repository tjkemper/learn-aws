# Messaging
* SQS
* SNS
* SES

## Simple Queue Service (SQS)
* Messaging queue service
* **Poll** model
* Unlimited number of messages
* Order not guaranteed; Messages can be received more than once
* Can set a *message visibility window* of up to 12 hours
* Can store messages between 1 minute and 2 weeks (default is 4 days)
* **Purge queue** to delete all messages in a SQS queue
* Can trigger autoscaling (with CloudWatch) based on number of messages in your queue

### Use cases
* Connect decoupled applications
* Offload work from primary services
* Configure Dead Letter Queue (DLQ)
  * Queue that receives messages from other queues
  * Typically used to isolate messages that could not be processed

## Simple Notification Service (SNS)
* **Push** Messaging Service *(pub/sub)*
* Publish **topics** to **subscriptions**
  * topics are logical names
  * subscriptions are endpoints that SNS can send messages to
* Access to topics can be managed by IAM
* Requests
  * Up to 256 KB
  * Charged in 64KB increments

### Subscriptions
* HTTP
* HTTPS
* Email
* Email-JSON
* Amazon SQS
* Application
* AWS Lambda

## Simple Email Service (SES)
* Email sending service
* Reliable, high delivery rates
* **Message:** one communication to one recipient
