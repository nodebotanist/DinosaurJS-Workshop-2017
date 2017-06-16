# Let's Create our IoT Device!

### 1. Modifying the bot code to call the lambda and use the output

We want to copy our original code and change the following:

1\) on button press, if we're not waiting for our lambda function to return already, call our lambda function

2\) When our function returns, strobe the light for the number of seconds that is returned

3\) Turn the LED off when the time has elapsed

#### a few hints

1\) You'll want to use [the request npm module](https://www.npmjs.com/package/request) to make the request to your lambda function

2\) Make sure you add a mechanism to stop the bot from calling if it's already waiting for the lambda

3\) console.log\(\) and the johnny-five REPL are your friends!

4\) Ask if you need help or get stumped



