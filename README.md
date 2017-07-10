# Serverless Retail Workshop.

This GitHub repository is an open-source workshop intended to accompany the core functional code in https://github.com/smartbiz/serverless-retail. For the workshop portion, participants take part in an interactive exercise playing the roles of merchants, photographers, and customers using hello-retail core.  After that, you extend it using this workshop to calculate the winning photographer and merchant.  Perhaps, afterwards, you can extend it in even more interesting ways for extra credit!

Serverless Retail is a 100% Serverless, Event-Driven Framework and Functional Proof-Of-Concept showcasing a central unified log approach as applied to the retail problem space. All code and patterns are intended to be re-usable for scalable applications large and small.

## Serverless Retail! core explained - an event-centric, serverless architecture
![Serverless all the things!](assets/images/serverless-retail-architecture.png)

## Technologies used for this workshop
* **AWS Lambda** One way of thinking about it is 'functions as a service.'
* **AWS Kinesis** The stream.  Technically a durable replicated log.
* **AWS API Gateway** A fully-managed web-service front-end.  Resources, methods, authentication.  Trigger lambdas to do the work.
* **AWS DynamoDB** NoSQL tables.  Used here as a simple key-value store.
* **Serverless.com Framework** is an open source project with lots of handy tools to manage serverless configurations, shared code, and deploy your work to AWS.

## Why?
Serverless architectures offer incredible promise to reduce code complexity, operations costs, improve scalability, and when used correctly, security.  When you go serverless, you quickly realize the power of event-driven architectures.  These architectures are impedance matched with stateless, event-driven AWS Lambda functions and AWS Step Functions fully managed state machines.  A complete systems architecture that takes advantage of a unified central log/stream has benefits to extensibility, simplicity, backup and restore, and databases-as-cattle.  This project attempts to explore and prove out some of these concepts in a production-ready and scalable format.

## What you'll build in this workshop
![Serverless all the things!](assets/images/serverless-retail-workshop.png)

In this diagram we see a lambda consuming from the stream and populating two DynamoDB tables.  The first keeps track of which merchants and photographers are associated with which products.  The second table maintains a tally of sales per merchant and sales per photographer.  The web service that is exposed through API Gateway invokes a lambda that reads from this aggregated view.

## What does all of this cost?
* AWS Lambda charges based on both the number of invocations and the duration of each function. For simple functions like these, assume about $.20 per million invocations.
* AWS API Gateway is about $3.50 per million calls.
* AWS DynamoDB for up to 5TPS in this example should cost less than $4 a month.

So, if we had 10,000,000 events a day (~200 events per second peak) and 1,000 reads from the web service, we'd expect about $2 in Lambda, $.0035 in API Gateway, and $10 a day in DynamoDB.

> **_Notes:_**
>
> According to our limited resources, we just support NodeJS in Mac OS and Ubuntu 16.04 LTS.


