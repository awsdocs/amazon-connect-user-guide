# Understanding Contact Flows<a name="contactflow"></a>

A contact flow is an editable roadmap directing the customer experience of the contact center from the time they enter the system to the end of the contact\.

You can create a contact flow using the contact flow templates provided\. You can also create your own contact flow from scratch, using the **Create contact flow** editor\.

The following template types are available:
+ **Customer queue flow**—Manages what the customer experiences while in queue, before being joined to an agent\. Customer queue flows are interruptible and can include actions such as an audio clip apologizing for a delay and offering an option to receive a callback, leveraging the **Transfer to queue** block\.
+ **Customer hold flow**—Manages what the customer experiences while the customer is on hold\. With this flow, one or more audio prompts can be played to a customer using the **Loop prompts** block while waiting on hold\.
+ **Customer whisper flow**—Manages what the customer experiences as part of an inbound call immediately before being joined with an agent\. The agent and customer whispers are played to completion, then the two are joined\.
+ **Outbound whisper flow**—Manages what the customer experiences as part of an outbound call before being connected with an agent\. In this flow, the customer whisper is played to completion, then the two are joined\. For example, this flow can be used to enable call recordings for outbound calls with the **Set call recording behavior** block\.
+ **Agent hold flow**—Manages what the agent experiences when on hold with a customer\. With this flow, one or more audio prompts can be played to an agent using the **Loop prompts** block while the customer is on hold\.
+ **Agent whisper flow**—Manages what the agent experiences as part of an inbound call immediately before being joined with a customer\. The agent and customer whispers are played to completion, then the two are joined\.
+ **Transfer to agent flow**—Manages what the agent experiences when transferring to another agent\. This type of flow is associated with transfer to agent quick connects, and often plays messaging, then completes the transfer using the **Transfer to agent** block\.
+ **Transfer to queue flow**—Manages what the agent experiences when transferring to another queue\. This type of flow is associated with transfer to queue quick connects, and often plays messaging, then completes the transfer using the **Transfer to queue** block\.

## Contact Block Definitions<a name="contact-blocks"></a>

Contact flows are created in the contact flow editor using action blocks arranged by dragging and dropping them onto a grid\. The contact flow configuration is grouped into blocks\. Each group represents a specific action, and each block has editable conditions related to the group’s action or behavior\.

**Note**  
When you set **User Defined** or **External** values in dynamic attribute fields, ensure that you use only alphanumeric characters \(A\-Z, 0–9\) and periods\. No other characters can be used\.

### Interact<a name="contact-interact"></a>


| Block | Action | Description | 
| --- | --- | --- | 
|  Play prompt  |  Plays audio\.  |  Prompts can be an audio file, stored in the prompt library, or text\-to\-speech, which can optionally be specified in a flow via a contact attribute\. If you use text\-to\-speech, you can use a maximum of 1,024 characters\.  | 
|  Get customer input  |  Branches based on customer intent\.  |  Plays an interruptible audio prompt and branches based on DTMF or Amazon Lex intents\. If you use text\-to\-speech, you can use a maximum of 1,024 characters\.  | 
|  Store customer input  |  Stores numerical input to contact attribute\.  |  Plays an interruptible audio prompt and stores digits via DTMF as a contact attribute\. To enable encryption, contact your system administrator to add a public signing key to the **Contact flow security keys** settings of your Amazon Connect instance\.  | 
|  Loop prompts  |  Loops a sequence of prompts while a customer or agent is on hold or in queue\.  |  When **Loop prompts** is used in a queue flow, audio playback can be interrupted with a flow at preset times\.  | 
|  Hold customer or agent  |  Places a customer or agent on or off hold\.  |  Settings: Agent on hold / customer on call Customer on hold / agent on call Agent and customer on call  | 

### Integrate<a name="contact-integrate"></a>


| Block | Action | Description | 
| --- | --- | --- | 
|  Invoke AWS Lambda function  |  Makes a call to AWS Lambda, and optionally returns key\-value pairs\.  |  The returned key\-value pairs can be used to set contact attributes\.  | 

### Set<a name="contact-set"></a>


| Block | Action | Description | 
| --- | --- | --- | 
|  Set queue  |  Specifies the queue to be used when **Transfer to queue** is invoked\.  |  A queue must be specified before invoking **Transfer to queue**\. It’s also the default queue for checking attributes, such as staffing, queue status, and hours of operation\. To use a Set queue block to set the queue dynamically, such as with contact attributes, you must specify the ARN for the queue rather than the queue name\. To find the ARN for a queue, open the queue in the queue editor\. The ARN is included as the last part of the URL displayed in the browser address bar after /queue\. For example, `.../queue/76f149bd-9edb-4128-b969-347f083d1501`\.   | 
|  Set call recording behavior  |  Sets options for call recordings\.  |  Enables or disables call recording for the agent, customer, or both\.  | 
|  Set contact attributes  |  Stores key\-value pairs as contact attributes\.  |  Contact attributes are accessible by other areas of Amazon Connect, such as the CCP and CTRs\.   | 
|  Change queue priority/routing age   |  Alters the priority of the contact in queue\.  |  Routing age alters the time in queue for the contact, which determines its priority in comparison to when other contacts are received\. Queue priority sets the contact to a high priority that can be compared to other contacts that have a priority set \(typically between 1 and 1000\)\.   | 
|  Set hold flow  |  Links from one contact flow type to another\.  |  Specifies the flow to invoke when a customer or agent is put on hold\.  | 
|  Set whisper flow  |  Overrides the default whisper by linking to a whisper flow\.  |  Specifies the whisper to be played to customer on an outbound call, or to the customer or agent when the call is joined\.  | 
|  Set callback number  |  Sets a callback number\.  |  Specifies the number to be used to call the customer back in the CCP, or when **Transfer to queue** is invoked with the callback option\. When specifying a phone number in Amazon Connect, the number must be in [E\.164 format](https://en.wikipedia.org/wiki/E.164)\. Numbers in E\.164 format do not include the leading zeroes you would dial for a local or regional call within the same country when dialing the number from a phone\. For example, if you usually dial 0400xxxxxx to place a call in Australia, the number in E\.164 format includes the country code of 61 and removes the leading zero for the number\. The number to use in Amazon Connect is **\+61400xxxxxx**\.  | 
|  Set agent status  |  This allows for the setting of an agent status via a contact flow\.  |  For example, you can use this with **Store customer input** to set the agent status to **On hold** so they don’t hear the input from the customer during credit card entry\.  | 
|  Set voice  |  Sets the voice\.  |  Sets the voice to interact with the customer, and optionally the voice if using text\-to\-speech \(TTS\)\.  | 
|  Set customer queue flow  |  Set queue flow\.  |  Specifies the flow to invoke when a customer is transferred to a queue\.  | 

### Branch<a name="contact-branch"></a>


| Block | Action | Description | 
| --- | --- | --- | 
|  Check queue status  |  Checks the status of the queue based on specified parameters\.  |  Branches based on the number of contacts, oldest contact in queue, or if the queue is at capacity\.  | 
|  Check staffing  |  Checks based on whether agents are available, staffed, or online\.  |  Branches based on whether agents are available, staffed \(available, on call, and after call work\), or online\.  You must set a queue before using a Check staffing block in your contact flow\. If a queue is not set, the block always proceeds through the error branch\. You can use a Set queue block to set the queue\. When a contact is transferred from one flow to another, the queue that is set in a contact flow is passed from that flow to the next one\.   | 
|  Check hours of operation  |  Checks to see whether the contact is within or outside of business defined hours\.  |  Branches based on specified hours of operation, either directly or as associated to a queue that is within open hours\.  | 
|  Check contact attributes  |  User\-based comparison checks\.  |  Branches based on a comparison to the value of a contact attribute\. Examples of supported comparisons include: **Equals**, **Is Greater Than**, **Is Less Than**, **Starts With**, **Contains**\.   | 
|  Distribute by percentage  |  Routes customers randomly based on a percentage\.   |  Like flipping a coin, contacts are distributed randomly, which doesn’t guarantee exact percentage splits\.   | 

### Terminate/Transfer<a name="contact-terminate"></a>


| Block | Action | Description | 
| --- | --- | --- | 
|  Disconnect / hang up  |  Terminates a customer contact\.  |  Disconnects the customer’s call\.  | 
|  Transfer to queue  |  Ends the current contact flow and places the customer in queue\.  |  A queue must be specified, using **Set queue**, before invoking **Transfer to queue**\. Optionally, the contact can be placed in queue to receive a callback, if **Set customer callback number** has been invoked\.  | 
|  Transfer to phone number  |  Transfers the customer\.  |  Ends the current contact flow and transfers the customer to a phone number\. If the country you want to select is not listed, you can submit a request to add countries you want to transfer calls to using the [Amazon Connect service limits increase form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-connect)\.  | 
|  Transfer to agent  |  Transfers the customer to an agent\.  |  Ends the current contact flow and transfers the customer to an agent\. If the agent is on a call, the contact is disconnected\.  | 
|  Transfer to flow  |  Transfers the customer to another flow\.  |  Ends the current contact flow and transfers the customer to a flow of the same type, such as customer queue flow, customer hold flow, customer whisper flow, agent hold flow, agent whisper flow, transfer to agent flow, and transfer to queue flow\.   | 
|  End flow/return from interruption  |  Ends the current flow without disconnecting the caller\.  |  This can be used to return to Loop prompts when it has been interrupted\. When **End flow/return from interruption** is invoked, the customer remains connected to the system\.  | 

## Creating Contact Flows<a name="create-contact-flow"></a>

You can create a variety of contact flows in Amazon Connect, such as transfer flows and interruptible flows\. The starting point for all contact flows is the contact flow editor\. You can make your contact flows as simple or complex as necessary\.

**To create a new contact flow in Amazon Connect using the editor**

1. Choose **Routing**, **Contact flows**, **Create contact flow**\.

1. Type a name and a description for your contact flow\.

1. Search for a block using the **Search** bar, or expand the relevant group to locate the block\.

1. Drag and drop blocks onto the canvas\. They don't have to be added in a specific order or sequence, as connections between the elements do not have to be strictly linear\.

1. Select the block title to access the settings and editing menu\.

**To create connections between blocks**

1. Select the originating group\.

1. Select the circle for the action to perform\.

1. Drag the arrow to the connector of the group that performs the next action\.
**Note**  
For groups that support multiple branches, drag the connector to the appropriate action\.

1. Repeat the steps to create a contact flow that meets your requirements\.

1. Choose **Save** to save a draft of the flow\. Choose **Publish** to activate the flow immediately\.
**Note**  
All connectors must be connected to a block in order to successfully publish your contact flow\.

A saved contact flow cannot be assigned to a number until it is published\.

## Contact Flow Logs<a name="contact-flow-logs"></a>

Amazon Connect contact flow logs provide you with real\-time details about events in your contact flows as customers interact with them\. You can use contact flow logs to help debug your contact flows as you are creating them\. After you publish your contact flows, you can view the logs to gain insight into what happens during complex contact flows, and quickly identify errors that your customers encounter when they connect to your contact center\.

Contact flow logs are stored in Amazon CloudWatch, in the same region as your Amazon Connect instance\. A log entry added as each block in your contact flow is triggered\. You can configure CloudWatch to send alerts when unexpected events occur during active contact flows\. As a contact center manager, you can aggregate data from contact flow logs to analyze performance of contact flows to optimize the experience you provide for your customers\. For more information about CloudWatch Logs, see the [Amazon CloudWatch Logs User Guide](http://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/)\.

### Enabling Contact Flow Logs<a name="contact-flow-log-entries"></a>

To start generating contact flow logs, enable contact flow logs for your Amazon Connect instance\. After you enable logs for your instance, logs are generated only for contact flows that include a **Set logging behavior** block with logging set to enabled\. You can control which flows, or parts of flows, logs are generated for by including multiple **Set logging behavior** blocks and setting logging to enabled or disabled as desired\. When you use a **Set logging behavior** block to enable or disable logging for a flow, logging is also enabled or disabled for any subsequent flow that a contact is transferred to, even if the flow does not include a **Set logging behavior** block\. To avoid having logging settings persist between flows, you should include a **Set logging behavior** block in the flow with logging enabled or disabled as desired for that specific flow\.

When you create a new Amazon Connect instance, you can enable Contact flow logs when you configure Data Storage settings\. If you already have an Amazon Connect instance, you can enable or disable Contact flow logs for your instance in the Amazon Connect console under **Contact flow** settings\. You are not charged for generating contact flow logs, but are charged for using CloudWatch for generating and storing the logs\. Free tier customers are charged only for usage that exceeds service limits\. For details about Amazon CloudWatch pricing, see [Amazon CloudWatch Pricing](https://aws.amazon.com/cloudwatch/pricing/)\.

**To enable contact flow logs for your Amazon Connect instance**

1. Open the Amazon Connect console\.

1. Choose the instance alias for the instance for which to enable contact flow logs\.

1. Choose **Contact flows**\.

1. Select **Enable Contact flow logs** and choose **Apply**\.

After you enable contact flow logs for your instance, you can enable logging for a flow by adding a **Set logging behavior** block\.

**To enable or disable contact flow logs for a contact flow**

1. Add a **Set logging behavior** block and connect it to another block in the flow\.

1. Open the settings for the block, and under **Logging behavior** do one of the following:

   Select **Enable** to turn on logging for the flow\.

   Select **Disable** to turn off logging for the flow\.

1. Choose **Save**\.

1. If you add a **Set logging behavior** block to a contact flow that is already published, you must publish it again to start generating logs for it\.

### Data Captured in Contact Flow Logs<a name="contact-flow-log-data"></a>

Log entries for contact flows include details about the block associated with the log entry, the contact ID, and the action taken after the steps in the block were completed\. Any contact interaction that occurs outside of the contact flow is not logged, such as time spent in a queue or interactions with an agent\. You can control which data is captured in contact flow logs by including a **Set logging behavior** block in your contact flow\. You can set the properties of the block to disable logging during the parts of your contact flow that interact with or capture sensitive data or customers’ personal information\.

If you use Amazon Lex or AWS Lambda in your contact flows, the logs show the entry and exit of the contact flow going to them, and include any information about the interaction that is sent or received during entry or exit\.

Because the logs also include the contact flow ID, and the contact flow ID stays the same when you change a contact flow, you can use the logs to compare the interactions with different versions of the contact flow\.

The following example log entry shows a Set queue block of a customer queue flow\.

```
{
    "Timestamp": "2017-11-09T12:17.898Z",
    "ContactId": "f0b21968-952b-47ba-b764-f29a57bcf626",
    "ContactFlowId": "arn:aws:connect:us-east-2:0123456789012:instance/d-92673ef055/contact-flow/b1d791cf-1264-42e3-9a73-62cbcb3c9a45",
    "ContactFlowModuleType": "SetQueue",
    "Events": {
        "Queue": [
            "arn:aws:connect:us-east-2:670047220557:instance/d-92673ef044/queue/f0300e43-9547-477c-b8ba-0bb7a72f7fa1"
        ]
    }
}
```

### Tracking Customers Between Contact Flows<a name="contact-flow-log-multiple-flows"></a>

In many cases, customer contacts interact with multiple contact flows in your call center, being passed from one contact flow to another to appropriately assist them with their specific issue\. Contact flow logs help you track customers between different contact flows, by including the ID of the contact in each log entry\. When a customer is transferred to a different contact flow, the ID for the contact associated with their interaction is included with the log for the new flow\. You can query the logs for the contact ID to trace the customer interaction through each contact flow\. In larger, high\-volume contact centers, there can be multiple streams for contact flow logs\. If a contact is transferred to a different contact flow, the log may be in a different stream\. To make sure that you are finding all of the log data for a specific contact, you should search for the contact ID in the entire CloudWatch log group instead of in a specific log stream\.

### Create Alerts for Contact Flow Log Events<a name="contact-flow-log-alerts"></a>

You can configure CloudWatch to define a filter pattern that looks for specific events in your contact flow logs and then creates an alert when an entry for that event is added to the log\. For example, you can set an alert for when a contact flow block goes down an error path as a customer interacts with the flow\. Log entries are typically available in CloudWatch within a short time, giving you near real\-time notification of events in contact flows\.

### Analyzing Contact Flow Logs with Amazon Kinesis<a name="contact-flow-log-kinesis"></a>

To perform analysis on your contact flow logs, you can set up an Amazon Kinesis stream to stream your contact flow log data from CloudWatch to a data warehouse service, such as Amazon Redshift\. You can combine the contact flow log data with other Amazon Connect data in your warehouse, or run queries to identify trends or common issues with a contact flow\.

## Contact Flow Import/Export<a name="contact-flow-import-export"></a>

You can export contact flows from and import contact flows into your Amazon Connect instance\. You can use exported contact flows to create backup copies and manage version control of your contact flows\. This lets you easily restore a previous version in case you encounter an error with a published contact flow\. You can easily copy contact flows from one Amazon Connect instance to another, for example from a test environment to a production environment, or from one region to another as you expand your customer service organization\.

**Note**  
The Contact Flow Import/Export feature is currently in Beta status\. Updates and improvements that we make could result in issues in future releases importing contact flows that are exported during the beta phase\.

Because Amazon Connect contact flows are not tied to a specific instance or account, exported flows could also be imported into instances created by other customers, allowing Amazon Connect partners to create custom contact flow solutions that can be used by Amazon Connect customers\.

When you export a contact flow, the most recently saved version of the flow you currently have open in the Contact Flow editor is exported as a UTF\-8 encoded JSON document\. Each block of your contact flow is included in the JSON document as a separate section\. To import a contact flow, either one that you previous exported, or that was exported from a different Amazon Connect instance, you just select the JSON file and import it\. The imported flow replaces the contact flow currently open in the editor\. The imported contact flow is not added to your Amazon Connect instance until you save it after importing\.

### Resolving Resources in Imported Contact Flows<a name="contact-flow-export-resources"></a>

When you create a contact flow, the resources you include in the contact flow, such as queues and voice prompts, are referenced within the contact flow using the name of the resource and the Amazon Resource Name \(ARN\)\. The ARN is a unique identifier for a resource that is specific to the service and region in which the resource is created\. When you export a contact flow, the name and ARN for each resource referenced in the contact flow is included in the exported contact flow\.

When you import a contact flow, Amazon Connect attempts to resolve the references to the Amazon Connect resources used in the contact flow, such as queues, by using the ARN for the resource\. When you import a contact flow into the same Amazon Connect instance that you exported it from, the resources used in the contact flow will resolve to the existing resources in that instance\. If you delete a resource, or change the permissions for a resource, Amazon Connect may not be able to resolve the resource when you import the contact flow\. When a resource cannot be found using the ARN, Amazon Connect attempts to resolve the resource by finding a resource with the same name as the one used in the contact flow\. If no resource with the same name is found, a warning is displayed on the block that contains a reference to the unresolved resource\.

If you import a contact flow into a different Amazon Connect instance than the one it was exported from, the ARNs for the resources used are different\. If you create resources in the instance with the same name as the resource in the instance where the contact flow was exported from, the resources can be resolved by name\. You can also open the blocks that contain unresolved resources, or resources that were resolved by name, and change the resource to another one in the Amazon Connect instance\. You can save a contact flow with unresolved or missing resources, but you cannot publish it until the resources are resolved or removed\.

### Exporting Contact Flows<a name="contact-flow-labels"></a>

When you export a contact flow, the JSON document created for the flow includes a section for each block in the flow\. The name used for a specific block, parameter, or other element of the contact flow may be different than the label used for it in the user interface \(UI\)\.

By default, contact flow export files are created without a file name extension, and saved to the default location set for your browser\. We suggest saving your exported contact flows to folder that contains only exported contact flows\.

**Important**  
When you attempt to import or export a large or complex contact flow, the export may fail if the contact flow contains a large amount of blocks and resources\. It may also fail if the file size for the exported contact flow exceeds 1 MB in size\. An notification message is displayed when this occurs\.

**To export a contact flow**

1. Log in to your Amazon Connect instance using an account that is assigned a security profile that includes view permissions for contact flows\.

1. Choose **Routing**, **Contact flows**\.

1. Open the contact flow to export\.

1. Choose **Save**, **Export flow**\.

1. Provide a name for the exported file, and choose **Export**\.

**To import a contact flow**

1. Log in to your Amazon Connect instance\. The account must be assigned a security profile that includes edit permissions for contact flows\.

1. Choose **Routing**, **Contact flows**\.

1. Do one of the following:
   + To replace an existing contact flow with the one you are importing, open the contact flow to replace\.
   + Create a new contact flow of the same type as the one you are importing\.

1. Choose **Save**, **Import flow**\.

1. Select the file to import, and choose **Import**\.

1. Review and update any resolved or unresolved references as necessary\.

1. To save the imported flow, choose **Save**\. To publish, choose **Save and Publish**\.