We have chosen what website we want to check and for which alerts. Now we should program the bot's functionality. Keep in mind that Python indentation is very important. Before you run the code plase make sure that your indentation is correct.

We're going to write all of our checks inside of a while loop. We do this because we want the bot to be doing these checks continuously while it is online. We also put everything inside of a try-except block to make sure that any errors that may appear are dealt with:

```
while True:
    try:
```
Now, we get the bot to try to connect to the chosen website (in our case Google)

```
        response = requests.get(url)
```
And we check that is has the right status code. The bot then sends an alert to the chosen channel about the status of the website
```
        if response.status_code != status_code:
            # Send an alert message to your Slack channel
            message = f"The server status has changed to {response.status_code}!"
            response = client.chat_postMessage(
                channel="#slack-bot",
                text=message
            )
            print("Alert sent: ", response["ts"])
        else:
            message = f"The server at {url} is up and running!"
            response = client.chat_postMessage(
                channel="#slack-bot",
                text=message
            )
            print("Alert sent: ", response["ts"])
```

Now that the checks are done, let us deal with the rest of the try-except block. In the case where the website sends a connection error, we send an alert warning that the website is down:
```
    except requests.exceptions.ConnectionError:
        print("Failed to connect to the server")
        message = f"The server at {url} is down or not responding!"
        response = client.chat_postMessage(
            channel="#slack-bot",
            text=message
        )
        print("Alert sent: ", response["ts"])
```
In the case of any other error we just print it in terminal

```
    except SlackApiError as e:
        print("Error sending message: ", e)
```

Finally, before the loop iteration is done, we make the program wait for 10 seconds before it starts a new one. You can change the time that passes between the checks to anything you want. This does mean that the bot will send a message every 10 seconds, so choose the sleeping time carefully:
```
    # Wait for 10 seconds before checking again
    time.sleep(10)  
```