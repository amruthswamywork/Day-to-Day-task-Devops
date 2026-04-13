#s3->eventbridge->lambda




import json
import boto3

s3 = boto3.client('s3')

BUCKET_NAME = "amruth-daily-read-bucket"

def lambda_handler(event, context):

    try:
        # List objects in bucket
        response = s3.list_objects_v2(Bucket=BUCKET_NAME)

        if 'Contents' not in response:
            print("No files found in bucket")
            return
        
        for obj in response['Contents']:
            key = obj['Key']
            print(f"Reading file: {key}")

            file_obj = s3.get_object(Bucket=BUCKET_NAME, Key=key)
            content = file_obj['Body'].read().decode('utf-8')

            print(f"Content of {key}:")
            print(content)

    except Exception as e:
        print("Error:", str(e))

    return {
        "statusCode": 200
    }