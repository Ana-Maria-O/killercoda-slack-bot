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
It is very easy to monitor multiple webistes or have a SlackBot send alerts for multiple specific status codes!