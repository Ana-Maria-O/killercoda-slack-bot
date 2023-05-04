If there are more webistes and/or status codes that you want to monitor, there is an easy easy way to do so. For this tutorial, in addition of checking ig Google is up, we want to check if YouTube sends a 503 error.

We begin by adding the URL and the status code at the top of the document, where we have the URL for Google and its status code:
```
url2 = "https://www.youtube.com/"
status_code2 = 503
```
Then we make a second try-except block in the while loop, and check for the status code. We print all errors in the console:
```
    try:
        response_yt = requests.get(url2)
        if response_yt.status_code == status_code2:
            # Send an alert message to your Slack channel
            message = f"YouTube is currently unavailable."
            response = client.chat_postMessage(
                channel="#<Your_Channel_Name>",
                text=message
            )
            print("Alert sent: ", response["ts"])
    except SlackApiError as e:
        print("Error sending message: ", e)

```
It is very easy to monitor multiple webistes or have a SlackBot send alerts for multiple specific status codes! Here is the code from the last step, with these additions:
```
import os
import time
import requests
from slack_sdk import WebClient
from slack_sdk.errors import SlackApiError

# Set the API token for your Slack bot
client = WebClient(token="<Your_Slack_Token_Here>")

# Define the URLs and status codes to check
url = "https://www.google.com/"
status_code = 200
url2 = "https://www.youtube.com/"
status_code2 = 503

# Periodically check the server status and send alerts to Slack
while True:
    try:
        response = requests.get(url)
        if response.status_code != status_code:
            # Send an alert message to your Slack channel
            message = f"The server status has changed to {response.status_code}!"
            response = client.chat_postMessage(
                channel="#<Your_Channel_Name>",
                text=message
            )
            print("Alert sent: ", response["ts"])
        else:
            message = f"The server at {url} is up and running!"
            response = client.chat_postMessage(
                channel="#<Your_Channel_Name>",
                text=message
            )
            print("Alert sent: ", response["ts"])
    except requests.exceptions.ConnectionError:
        print("Failed to connect to the server")
        message = f"The server at {url} is down or not responding!"
        response = client.chat_postMessage(
            channel="#<Your_Channel_Name>",
            text=message
        )
        print("Alert sent: ", response["ts"])
    except SlackApiError as e:
        print("Error sending message: ", e)

    try:
        response_yt = requests.get(url2)
        if response_yt.status_code == status_code2:
            # Send an alert message to your Slack channel
            message = f"YouTube is currently unavailable."
            response = client.chat_postMessage(
                channel="#<Your_Channel_Name>",
                text=message
            )
            print("Alert sent: ", response["ts"])
    except SlackApiError as e:
        print("Error sending message: ", e)

    # Wait for 10 seconds before checking again
    time.sleep(10)
```