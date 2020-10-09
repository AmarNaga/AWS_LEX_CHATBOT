# AWS_LEX_CHATBOT
**STEPS**
1. Create a chatbot without lambda function for now(will configure later) to test out the bot.
2. Install NodeJs and Serverless in the system.
-->(npm install -g serverless)
--> Visit: serverless.com/framework/docs/providers/aws/guide/installation/
3. Copy paste the aws cli info from vocareum workbench in awseducate account to .aws/credentials
4. In cmd
--> aws configure
--> Enter.....
5. Create a folder chatbot workspace (in desktop)
--> mkdir chatbot
--> cd chatbot
--> serverless create --template aws-nodejs --path my-bot (to start the serverless service)
--> cd my-bot (actual serverless workspace)
--> code . (open in vs code)
6. In serverless.yml file, in functions: change the name hello to your function name (getWeather)
7. In handler.js, clear all 
--> copy handler.js code from github and paste it in the handler.js in the my-bot workspace
8. Here, In return funtion,the sessionAttribute provides the session in fo from the bot. In dialogAction type defines the action AWS lex responds to. Type close means no reply is expected after the invocation of the return type and hence ends the conversation
   Message section is where we send the message to the user. The message constraints is sent through the API call(view in "const answer").
   Visit : openweathermap.org documentation for more information on weather API
   It takes in City variable form user and finds the value through api url.
   Temperature and Humidity information are extracted.
9. Change dialogAction type to "confirmIntent" to call other Intent.
   To get more information or provide more info to the user Call different Intents.
10. Install dependencies axios : In terminal: "npm i axios"
11. Use serverless to deploy the function: serverless deploy
12. If the error is shown as: 
	serverless : File C:\Users\amarn\AppData\Roaming\npm\serverless.ps1 cannot be loaded because running scripts is disabled on this system. For more 
	information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
 Then, run: "Set-ExecutionPolicy -Scope Currentuser -Executionpolicy Unstricted "
 This error occur when the current user have an undefined ExecutionPolicy
 Then run : "serverless deploy"
13. Reminder: The aws cli info expires every 1 hour so, make sure to reconfigure the information in .aws/credentials
14. Copy the function name (eg: my-bot-dev-getWeather)
15. Go to Amazon lex. Refresh the page .
16. Now we add Lambda function under Fulfillment section . Choose the function we just created (my-bot-dev-getWeather). (The Lambda function won't show unless you refresh the page)
17. Save and Build the bot
18. Add more intents as necessary.
	THE WEATHER BOT IS HENCE BUILT WITH AWS LEX.
Embed the bot to the web or other software of you choice.
