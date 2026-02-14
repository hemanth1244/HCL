Serverless – Lambda + API Gateway (Hello World API)
Deploy your first API.
Steps:
Go to Lambda → Create function
Use code:
def lambda_handler(event, context):
    return {"message": "Hello from Lambda"}
Create API Gateway → HTTP API
Connect Lambda as integration
Deploy
Test API URL in browser
<img width="1780" height="806" alt="image" src="https://github.com/user-attachments/assets/7a8be749-43a5-4976-8d9d-c1d925fb29a3" />


