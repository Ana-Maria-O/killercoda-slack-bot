This step is here to ensure that you have the proper setup to run and test the SlackBot we will be making. If you want to create your own server, then follow the steps described below.

If you are a TA for the DevOps course, check the email sent on the course email by amolt@kth.se. There are an invitation to a pre-made slack server and an API key that will be required later. Once you have the key and have entered the slack channel, you can move on to the next step.

## 1: Open slack API console. (https://api.slack.com/).

## 2: Click on “Your apps”.
![gitkey](./jpgs/1.jpg)
## 3: Click on “Create New App”.
![gitkey](./jpgs/2.jpg)
## 4: Click on “From scratch”.
![gitkey](./jpgs/3.jpg)
## 5: Now give your app name and select workspace then click on the “Create App” button.
![gitkey](./jpgs/4.jpg)
## 6: Click on the “App Home” button and click on “Review Scopes to Add”.
![gitkey](./jpgs/5.jpg)
## 7:  After clicking on the “Review Scope to Add” button, scroll down and find the Scope section. Then click on the “Add an OAuth Scopes” Button under “Bot Token Scopes” and add “chat: write” as shown in the below image.
![gitkey](./jpgs/6.jpg)
## 8: Now click on “Install to Workspace” and press on “Allow” to generate an OAuth token.
![gitkey](./jpgs/7.jpg)
## 9: Now copy the above “OAuth Token” and have it prepared for the following steps

## 10: Now we create the channel in slack and add our app to it. To open your slack account go to the channel bar and click on the “+” sign. Then click on “Create a new channel”.
![gitkey](./jpgs/8.jpg)
## 11: Now type your channel name and click on the “Create” Button.
![gitkey](./jpgs/9.jpg)

## 12: Now Add your app to the channel by just typing “/invite @Your_App_Name” (use the app name that you want to connect with the channel) in channel chat.
