# api-gateway-lambda-rds-project
1. Overview
This system uses a serverless architecture built with AWS services to host a dynamic web
application.
It connects a frontend webpage to a backend Lambda function that interacts with a MySQL
database (RDS).
The entire application is accessed through a custom domain configured in Route 53 and distributed
globally via CloudFront.
2. Components Involved
• Amazon RDS (MySQL): Stores user data and acts as the database.
• AWS Lambda: Executes backend logic and connects securely to RDS.
• Amazon API Gateway (REST API): Provides HTTP endpoints for Lambda.
• Amazon CloudFront: Delivers frontend and API content globally with caching.
• Amazon Route 53: Handles domain routing to CloudFront.
• Frontend (index.html): User interface that interacts with the REST API.
3. Overall Workflow
Step 1 – User opens the application via Route 53 domain.
Step 2 – CloudFront forwards the request to API Gateway (REST API).
Step 3 – API Gateway triggers the Lambda function.
Step 4 – Lambda connects securely to RDS (MySQL) using pymysql.
Step 5 – Lambda executes SQL queries.
Step 6 – API Gateway sends the response back via CloudFront to the user.
4. Data Flow Summary
1. User Browser – Sends a request (POST/GET)
2. Route 53 – Routes the request to CloudFront
3. CloudFront – Forwards request to API Gateway
4. API Gateway – Invokes Lambda
5. Lambda – Interacts with RDS
6. RDS – Processes and stores data
7. Lambda → API Gateway → CloudFront → Browser – Returns final response
5. Key Functional Roles
Frontend: Sends requests using fetch() and displays results.
API Gateway: Exposes Lambda via REST API endpoints.
Lambda: Handles  logic and database connectivity.
RDS: Stores persistent data within VPC.
CloudFront: Accelerates content delivery worldwide.
Route 53: Maps domain names to CloudFront distribution.
6. Benefits
• Serverless and auto-scaling
• Secure (VPC and HTTPS)
• Low latency with caching
• Cost-effective pay-per-use model
• Simplified REST-based communication
7. Example Flow (Registration Use Case)
• User fills registration form on index.html
• Browser sends POST request to API Gateway REST endpoint
• Lambda function runs SQL insert into RDS
• Lambda returns a success message to frontend
• CloudFront caches response, Route 53 routes domain
8. Conclusion
This architecture delivers a complete, scalable, and secure AWS-based serverless web application.
It leverages RDS, Lambda, REST API Gateway, CloudFront, and Route 53 for seamless data flow
from backend to frontend.



