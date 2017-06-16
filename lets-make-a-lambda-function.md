# Let's Make a Lambda Function!

Okay so to hook our robot up to the internet, we're going to create an AWS Lambda Serverless function.

### 1. Setup

First, on your computer, install the serverless framework CLI:

[https://serverless.com](https://serverless.com)

Then follow these instructions for setting up AWS Lambda:

[https://serverless.com/framework/docs/providers/aws/guide/credentials/](https://serverless.com/framework/docs/providers/aws/guide/credentials/)

[https://serverless.com/framework/docs/providers/aws/guide/quick-start/](https://serverless.com/framework/docs/providers/aws/guide/quick-start/)

### 2. Create your serverless function

Move to a folder you don't mind putting code projects in and run

```
serverless create --template aws-nodejs --path dinojs-lambda
```

This will create a few files in a folder called dinojs-lambda, so let's dive in

```
cd dinojs-lambda && ls
```

You'll see a serverless.yml file, and a handler.js file. For now, we're going to deploy this and invoke it to make sure it works:

### 3. Test Deploy 

```
serverless deploy
```

\(this'll take a minute...\)

```
serverless invoke -f hello
```

You should get back:

```
{
    "statusCode": 200,
    "body": "{\"message\":\"Go Serverless v1.0! Your function executed successfully!\",\"input\":{}}"
}
```

### 4. Get the HTTP url

Login to the [AWS Management Console](https://aws.amazon.com/console/)

In the AWS services search box, type 'Lambda' and click 'Lambda' when it appears.

Click on your function \(should be dinojs-lambda-dev-hello\)

Click on the 'Triggers' tab

Click the grey outlined box and select API Gateway

Set Security to 'Open' \(Note: don't do this in the real world!\)

Hit 'Submit.' You'll see a URL under API Gateway:xxxxxx. Click it to make sure you see:

```
{"message":"Go Serverless v1.0! Your function executed successfully!","input":{"resource":"/dinojs-lambda-dev-hello","path":"/dinojs-lambda-dev-hello","httpMethod":"GET","headers":{"Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8","Accept-Encoding":"gzip, deflate, br","Accept-Language":"en-US,en;q=0.8","CloudFront-Forwarded-Proto":"https","CloudFront-Is-Desktop-Viewer":"true","CloudFront-Is-Mobile-Viewer":"false","CloudFront-Is-SmartTV-Viewer":"false","CloudFront-Is-Tablet-Viewer":"false","CloudFront-Viewer-Country":"US","dnt":"1","Host":"7bmmod4zbg.execute-api.us-east-1.amazonaws.com","Referer":"https://console.aws.amazon.com/lambda/home?region=us-east-1","upgrade-insecure-requests":"1","User-Agent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.86 Safari/537.36","Via":"2.0 d374cf8ba9fb40328599cb9523787801.cloudfront.net (CloudFront)","X-Amz-Cf-Id":"hZNxf1apM2FTYIr7wyEP1gbslmAlCAiMM1a4iv4N0Wvh4FMllxhWFQ==","X-Amzn-Trace-Id":"Root=1-59435ec9-002a65c21067e7b9554ee042","X-Forwarded-For":"71.205.153.208, 54.182.238.48","X-Forwarded-Port":"443","X-Forwarded-Proto":"https"},"queryStringParameters":null,"pathParameters":null,"stageVariables":null,"requestContext":{"path":"/prod/dinojs-lambda-dev-hello","accountId":"007381580642","resourceId":"tj5ot3","stage":"prod","requestId":"768e51e4-524c-11e7-a5b2-655ac4877185","identity":{"cognitoIdentityPoolId":null,"accountId":null,"cognitoIdentityId":null,"caller":null,"apiKey":"","sourceIp":"71.205.153.208","accessKey":null,"cognitoAuthenticationType":null,"cognitoAuthenticationProvider":null,"userArn":null,"userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.86 Safari/537.36","user":null},"resourcePath":"/dinojs-lambda-dev-hello","httpMethod":"GET","apiId":"7bmmod4zbg"},"body":null,"isBase64Encoded":false}}
```

If so, then copy that URL-- we'll be using it with our robot in a bit. First, let's make our lambda function return something we can use. 

### 5. Modify the Lambda Function

In our case, we're going to have it return a random number between 1 and 10, which will be the number of seconds the light flashes after we push the button.

Change your handler.js to match:

```
module.exports.hello = (event, context, callback) => {
  let randomNumber = Math.ceil(Math.random() * 9)

  const response = {
    statusCode: 200,
    body: JSON.stringify({
      numSeconds: randomNumber
    }),
  };

  callback(null, response); 
```



