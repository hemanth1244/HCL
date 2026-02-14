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
<img width="1790" height="804" alt="image" src="https://github.com/user-attachments/assets/27dea087-c6a2-49f2-8f88-8bd94c9dd67e" />
<img width="1898" height="807" alt="image" src="https://github.com/user-attachments/assets/8f9119f0-3a4d-4ea6-8eef-625566eecc52" />
<img width="1733" height="345" alt="image" src="https://github.com/user-attachments/assets/b58fb3be-b9c8-409b-bab8-e1cdd0f05807" />
<img width="1777" height="672" alt="image" src="https://github.com/user-attachments/assets/0f067031-97fb-4458-a1e5-d05863e15612" />
<img width="1780" height="499" alt="image" src="https://github.com/user-attachments/assets/9e292140-7ae9-438e-9a49-87133c5adc0d" />
<img width="1770" height="578" alt="image" src="https://github.com/user-attachments/assets/b498bdea-3147-41d6-be40-68c6a3c4b4cd" />
<img width="1898" height="806" alt="image" src="https://github.com/user-attachments/assets/405e211d-46f4-4c67-917b-6da55353204a" />
<img width="1890" height="711" alt="image" src="https://github.com/user-attachments/assets/3e621a26-328d-483c-9f9a-926dfa816e90" />
<img width="818" height="125" alt="image" src="https://github.com/user-attachments/assets/1edd0538-8da1-4e4d-a85c-4ec4beb86f84" />

I created a Lambda function and integrated it with API Gateway HTTP API. After deploying to a stage, I accessed the invoke URL with the route path, which triggered Lambda and returned the Hello World response.











