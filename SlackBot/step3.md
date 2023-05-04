Now open the file named bonjour.py that we paste the SLACK_TOKEN before.

Starting by importing slack:

``` import slack  ```

Under that we have the SLACK_TOKEN:
``` SLACK_TOKEN="<Your Token>”.  ``` 

Then we initialize a Slack client with our token, and send a "Bonjour"
message to our channel in Slack.
```
client = slack.WebClient(token=SLACK_TOKEN)
client.chat_postMessage(channel='#<channel_name_for_the_bot>',text='Bonjour')
``` 

Run the script and go to your Slack channel and check that it works.