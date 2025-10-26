# ☁️ Task 4: Deploy a Serverless Function to the Cloud

---

## 🎯 Objective
To understand **serverless computing** by creating and deploying a **cloud function (FaaS)** that automatically executes code when triggered — without managing any servers.  
This demonstrates **event-driven computing**, **resource optimization**, and **cost-effective automation**.

---

## 🧩 Function Name
**task-4**

---

## 🛠️ Tools Used
- **AWS Lambda** (via AWS Free Tier)  
- **AWS API Gateway** (for HTTP trigger)  
- **VS Code** (for editing function code)  
- **Postman / Web Browser** (for testing the endpoint)

---

## 📂 Source Code (`lambda_function.py`)

```python
import json

def lambda_handler(event, context):
    try:
        # Query parameters from API Gateway (if present)
        params = event.get('queryStringParameters', {})
        name = params.get('name', 'Guest') if params else 'Guest'
        
        # Custom message
        message = f"Hello,HR Welcome to Serverless Cloud Function."
        
        # Return JSON response
        return {
            'statusCode': 200,
            'headers': {
                'Content-Type': 'application/json'
            },
            'body': json.dumps({
                'success': True,
                'message': message,
                'function': 'task-4 Lambda Function',
                'author': 'Rajani Ankush Jambhale'
            })
        }

    except Exception as e:
        # Error handling
        return {
            'statusCode': 500,
            'headers': {
                'Content-Type': 'application/json'
            },
            'body': json.dumps({
                'success': False,
                'error': str(e)
            })
        }

🧠 How It Works

1.AWS Lambda executes this code automatically whenever the API Gateway endpoint is hit.
2.The Lambda environment is fully managed — no servers, no manual scaling.
3.Function reads query parameters (like ?name=Rajani) and returns a formatted JSON response.
4.Ideal for lightweight APIs and event-based tasks.

🏁 Outcome

1]Learned how to deploy a Serverless Function using AWS Lambda.
2]Understood Function-as-a-Service (FaaS) and event-driven architecture.
3]Connected Lambda with API Gateway to make it accessible as an HTTP endpoint.
4]Tested real-time cloud execution and JSON response handling.
5]Experienced how serverless removes infrastructure management overhead.
6]Built a foundation for automated cloud-based microservices.
