# Let's Make a Lambda Function!

Okay so to hook our robot up to the internet, we're going to create an AWS Lambda Serverless function.

First, on your computer, install the serverless framework CLI:

[https://serverless.com](https://serverless.com)

Then follow these instructions for setting up AWS Lambda:

[https://serverless.com/framework/docs/providers/aws/guide/credentials/](https://serverless.com/framework/docs/providers/aws/guide/credentials/)

[https://serverless.com/framework/docs/providers/aws/guide/quick-start/](https://serverless.com/framework/docs/providers/aws/guide/quick-start/)

Move to a folder you don't mind putting code projects in and run

```
serverless create --template aws-nodejs --path dinojs-bot
```

This will create a few files in a folder called dinojs-bot, so let's dive in

```
cd dinojs-bot && ls
```



