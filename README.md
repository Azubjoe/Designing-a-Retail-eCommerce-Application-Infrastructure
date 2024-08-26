# Designing-a-Retail-eCommerce-Application-Infrastructure
Designing a system for a retail e-commerce application that needs to handle and process customer orders in real-time. The application must be able to receive, process, and fulfill orders while also updating various systems such as inventory management, customer notifications, and financial transactions.


## Architecture Overview

This system is built with the thinking that integrating with a third-party cloud-based ecommerce application will help to easily compose and customize functionalities, Speed time to launch, and lower cost as there is no infrastructure to manage or maintain.

## Reference Architecture
Refer to the 'Architecure Diagram' file in the repository

## Resources Used

1. User management is handled serverless and easily by using Amazon Cognito

2. Static parts of the frontend such as web pages and images are hosted on Amazon Simple Storage Service (Amazon S3) and delivered through Amazon CloudFront with low latency. 

3. Microservices architecture is leveraged by running our business logic in containers using Amazon Elastic Container Service (Amazon ECS) paired with a load balancer to manage customer requests traffic and auto scaling. Alternatively, AWS Lambda can be used to run code in serverless functions. 

4. Business logic is integrated with ecommerce applications APIs to gain flexibility when composing our shopping experience.

5.  We can deploy Amazon RDS and/or DynamoDB to serve as data stores for business data. For example, SQL is best fit for customer data and NoSQL is best fit to store products information. 

6. Events from ecommerce applications (such as new orders) are distributed to the applications asynchronously using Amazon EventBridge.

7. Amazon Simple Queue Service (Amazon SQS) receives events from EventBridge and queues them for processing by downstream services. 

8. Amazon S3 is used as a data lake for storing ecommerce applications events ingested through Amazon Kinesis Data Firehose, the data is used for visualizations, forecasting, and analyzing usage patterns. 

9. With Amazon Personalize, data such as previous buying behavior can be used to tailor customers’ shopping experience. 

