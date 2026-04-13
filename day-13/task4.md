APIGATEWAYS->LAMBDA_FUNCTIONS->SNS_TOPICS->SQS_QUEUES->LAMBDA_FUNCTIONS->S3(TRIGGER)->

body :


{
    "message": "pending"
    }


all task completed The above architecture represents a serverless application that processes incoming API requests, sends notifications to users, and triggers actions based on events in an S3 bucket.

work flow as follows:
worked on POC (4-task) work flow ,
a)API->LAMBDA-SNS ,
 b) API->LAMBDA->S3-SNS ,
 c) S3->EVENTBRIDGE ->LAMBDA->CRON , 
 d) LAMBDA-> S3(word search) -> SNS  