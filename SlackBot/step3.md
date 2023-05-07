Let us check that the bot has been configured correctly on Slack. Create a python file:

```
touch bonjour.py
```{{exec}}
Open the newly made file. It is time to start coding!

Inside the file begin by importing slack

```
import slack  
```

Under that, we are going to create a SLACK_TOKEN variable. This contains the API token that you have received via email (or have gotten after setting up the bot in Slack):
``` 
SLACK_TOKEN="<Your Token>”.  
``` 

Then we initialize a Slack client with our token, and send a "Bonjour"
message to our channel in Slack. In this example we are using the channel "#slack-bot", but feel free to replace that with the channel that you bound your bot to.
```
client = slack.WebClient(token=SLACK_TOKEN)
client.chat_postMessage(channel='#slack-bot',text='Bonjour')
``` 

Run the script, go to your Slack channel and check that it works.
```
python bonjour.py
```{{exec}}