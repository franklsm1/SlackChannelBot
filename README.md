# Slack Channel Bot Description
### A Slack channel bot built with Node-RED on IBM Bluemix

The bot will make a post in the specified channel every time a new channel is created (exluding private and archived channels). The post will let everyone know the name and any info that was provided about it.

##### An example channel bot output (with a link to the channel):
![alt tag](https://github.com/franklsm1/SlackChannelBot/blob/master/exampleBot2.PNG)

# Slack Channel Bot Import and Setup
##### 1.) Copy the contents of the channelBot.json file into your Node-RED editor using the import clipboard feature.

![alt tag](https://github.com/franklsm1/SlackChannelBot/blob/master/import.PNG)


##### After importing your flow should look similar to this:
![alt tag](https://github.com/franklsm1/SlackChannelBot/blob/master/nodeFlow.PNG)

##### 2.) Next you will need to update the 4 nodes outlined in red from the above image.
  
  -For the "Get Slack Channel List" node you will need to create a new slack bot, https://my.slack.com/services/new/bot, and then replace the text "<Slack API Bot Token Goes Here>" with the API token you are given for your bot into the node.
  
  -For the "Slack Response" node you will need to enable incoming webhooks for your slack team if you have not done so already, https://my.slack.com/services/new/incoming-webhook/. Then you will need to replace the text of the URL field, "<Slack Incoming Webhook URL Goes Here>", with the Webhook URL that was created for you.
  
  -For both of the "Channel count message" and "Update channel count" Cloudant DB nodes you will need to select the cloudant DB service that is running with your Node.js application and update the database name that is setup for your service (if using the Node-Red boilerplate in Bluemix the default name of the database is "nodered").
  
##### 3.) Next you will need to create a new document inside your cloudant DB with the following properties:
  
  {
    "_id": "channelCount",
    "count": 0
  }
  
  -The count value can be left at 0 (the bot will make an initial post to update the value) or you can set it to your current channel count (not including archived and private channels)
  
##### 4.) Finally deploy the application and your slack bot is up and running!
