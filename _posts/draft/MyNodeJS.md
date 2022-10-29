# NodeJS for Prod

## API Development

### RESTful



### GraphQL



### Unit test



### Typical Bug

1. file loop reference

2. Try/Catch fail on catching error in closure ( async )
3. 





## JS Mastery

### JS OOP

### JS Functional Programming

LISP-REPL-JS-DEN



## Infrastructure Mastery

### AWS Certification

- AWS Certified Solution Architect - Associate



### [AWS learn- Build Web App with S3 Lambda Api-Gateway DynamoDB](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/?e=gs2020&p=fullstack)

#### TOC

1. [Host a static website with S3](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/module-one/?e=gs2020&p=build-a-web-app-intro) (10 minutes).
2. [Building serverless function with Lambda.](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/module-two/?e=gs2020&p=build-a-web-app-intro) (5 minutes)

- Create a Lambda function from scratch using the AWS console (in Python, JavaScript, or Java)
- Create (JSON) events in the AWS console to test your function

1. [Link Serverless Function to Website](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/module-three/?e=gs2020&p=build-a-web-app-intro) (5 minutes): Deploy your serverless function with API Gateway.
2. [Create Data Table](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/module-four/?e=gs2020&p=build-a-web-app-intro) (10 minutes): Persist data in an Amazon DynamoDB table.
3. [Add Interactivity to Website](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/module-five/?e=gs2020&p=build-a-web-app-intro) (5 minutes): Modify your static website to invoke your API.

#### [Host Static Website with S3](https://aws.amazon.com/getting-started/hands-on/build-web-app-s3-lambda-api-gateway-dynamodb/module-one/?e=gs2020&p=build-a-web-app-intro)

Goal: configure S3 to host the static resources for your web application.

> Price: S3 free tier is 12 month on standard 5GB. I already over 12 month. So I will pick `S3 - One Zone-IA`. (99.5% A is high enough for a portfolio website.)

- `URL`: We temporally use a `website endpoint URL` that Amazon S3 supplies: `http://{your-bucket-name}.s3-website.{region}.amazonaws.com` 

- All static web content - including HTML, CSS, JavaScript, images, and other files - will be stored in Amazon S3. 





##### Config Block public access (bucket settings)

1. **Unselect** "**Block *all* public access**." Since we are hosting a website, we want people to have access to it.
2. **Select** the check box next to "Block public access to buckets and objects granted through new public bucket or access point policies."
3. **Select** the check box next to "Block public and cross-account access to buckets and objects through any public bucket or access point policies."
4. **Select** the check box to acknowledge that the content of this bucket might become public. We won't store any private information in this bucket as its contents could be public. This is what it should look like:

This is what it should look like:

<img src="https://raw.githubusercontent.com/hbxz/picture-storage/master/2020/07/Full%20Stack%20tutorial%20bucket%20settings.9081d2ac834fb1562cf41263385795eebb806431-20200714161620882.png" alt="Full Stack tutorial bucket settings" style="zoom: 33%;" />

> I'm not familiar with the diffence between these four policies.







### [AWS learn - Build React App with Amplify GraphQL](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/?e=gs2020&p=frontend)

> You will be building this React application using the Command Prompt/Terminal, test editor, and AWS Web Console. It consist of five short modules:

1. [Deploy and Host a React App](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-one/?e=gs2020&p=build-a-react-app-intro) (10 minutes): Create a React app and deploy and host through AWS Amplify.
2. [Initialize a Local App](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-two/?e=gs2020&p=build-a-react-app-intro) (5 minutes): Initialize a local app using AWS Amplify.
3. [Add Authentication](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-three/?e=gs2020&p=build-a-react-app-intro) (10 minutes): Add auth to your application.
4. [Add a GraphQL API and Database](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-four/?e=gs2020&p=build-a-react-app-intro) (15 minutes): Create a GraphQL API.
5. [Add the Ability to Store Images](https://aws.amazon.com/getting-started/hands-on/build-react-app-amplify-graphql/module-five/?e=gs2020&p=build-a-react-app-intro) (10 minutes): Add storage to your app.



### [Build a serverless app on AWS](https://www.linkedin.com/learning/building-serverless-apps-on-aws-2/next-steps?u=2087740)



##### 