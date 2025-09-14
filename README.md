# AWS Translation Bot
This project is a serverless multi-language translation chatbot built on AWS. 

## 🎥 Demo

Here’s a quick look at my **AWS Translation Bot** in action:  

![Bot Demo](assets/demo.gif)  

👉 [Watch the full demo on YouTube](https://youtu.be/yBXSPX7Dyuk)
## Architecture

User → Amazon Lex V2 → AWS Lambda (Python) → Amazon Translate → Response back to Lex → User
                   ↘︎ CloudWatch Logs (Monitoring)
The solution leverages a fully serverless design:

1. **Amazon Lex V2** – Captures user input, interprets intents, and triggers fulfillment.  
2. **AWS Lambda (Python 3.12)** – Acts as the fulfillment code hook. Handles slot data, invokes Amazon Translate, and returns translated text back to Lex.  
3. **Amazon Translate** – Provides language translation service.  
4. **Amazon CloudWatch** – Logs events, errors, and metrics for debugging and monitoring.  
5. **IAM Roles & Policies** – Securely allow Lex to invoke Lambda and Lambda to call Amazon Translate.

6. ## Features
- **Natural Language Understanding** with Lex intents and slots.
- **Custom Lambda Fulfillment** written in Python.
- **Multi-language Translation** using Amazon Translate API.
- **Cloud-native, serverless** and scalable design.
- **Error Handling & Logging** integrated with CloudWatch.

## Tech Stack
- **AWS Services**: Amazon Lex V2, AWS Lambda, Amazon Translate, IAM, CloudWatch  
- **Language**: Python 3.12  
- **Infrastructure**: Serverless (fully managed AWS services)  

## Setup
1. **Create Lambda Function**  
   - Runtime: Python 3.12  
   - Add permissions: `TranslateText`, `CloudWatch Logs`, and allow Lex to invoke.  

2. **Deploy Lambda Code**  
   Upload the `lambda_function.py` (see code in repo).  

3. **Configure Amazon Lex**  
   - Create a bot with an intent (`TranslateText`).  
   - Add slots: `Text`, `LanguageCode`.  
   - Enable fulfillment with the Lambda function.  

4. **Test & Debug**  
   Use the Lex test console. Monitor errors via **CloudWatch Logs**.
