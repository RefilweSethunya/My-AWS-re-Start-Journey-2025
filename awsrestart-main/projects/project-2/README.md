## Project 2
# Interactive Chatbot on AWS

## Project Overview
The goal of this project was to design and deploy an **interactive, AI-powered chatbot** using AWS services.  
The chatbot was built to simulate real-world customer support use cases — allowing users to **ask questions, receive automated responses, and trigger actions** via natural language processing.  
It demonstrates the use of **AWS Lex**, **Lambda**, and **API Gateway** for a fully serverless conversational workflow.  

---

## Business & Technical Requirements
- **Natural Language Understanding (NLU):** Ability to process varied user inputs and map them to specific intents.  
- **Serverless Infrastructure:** Fully managed and scalable components with minimal maintenance overhead.  
- **Integration Flexibility:** Ability to integrate with APIs, email, or databases for real-time data-driven responses.  
- **Cost Efficiency:** Pay-per-request model using AWS serverless compute and managed services.  
- **Extensibility:** Easy to add new intents, utterances, and fulfillment logic without rearchitecting the system.  

---

## Architecture Diagram

*Click to view the zoomable SVG version.*  
[<img src="lexchatbot.drawio.png" alt="Interactive Chatbot Architecture" width="800"/>](lexchatbot.drawio.svg)  

---

## Key AWS Services Used
- **Amazon Lex** – Conversational interface with natural language processing for intents and utterances  
- **AWS Lambda** – Serverless compute to handle intent fulfillment and backend logic  
- **Amazon API Gateway** – Secure REST endpoints for integration with external systems  
- **Amazon S3** – Static website hosting and storage for conversation logs or assets  
- **Amazon Polly** – Converts chatbot responses into realistic speech for a voice-capable experience  
- **Amazon CloudWatch** – Monitors chatbot performance and logs conversation activity  
- **AWS IAM** – Manages permissions and roles for secure interaction among services  

---

## Architecture Highlights
- End-to-end **serverless architecture** leveraging AWS Lex, Lambda, and API Gateway  
- **Scales automatically** to handle thousands of concurrent chatbot sessions  
- **Polly integration** adds optional voice capability for more engaging interactions  
- **CloudWatch logging** provides visibility into performance and user behavior  
- **IAM roles and policies** enforce secure access and least privilege  
- **Extensible design** — new intents and utterances can be easily added for expanded functionality  

---

## Learning Outcomes
Through this project I practiced:  
- Building and deploying a **serverless chatbot** architecture on AWS  
- Implementing **intent-based workflows** and integrating them with backend Lambda logic  
- Configuring **API Gateway** endpoints for real-time chatbot communication  
- Enhancing user experience using **Amazon Polly and Lex** voice/text features  
- Monitoring, logging, and analyzing chatbot interactions with **CloudWatch**  
- Applying the principles of **scalability, security, and cost optimization** in a serverless context  

