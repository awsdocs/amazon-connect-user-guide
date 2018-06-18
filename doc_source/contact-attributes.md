# Amazon Connect Contact Attributes<a name="contact-attributes"></a>

**Topics**
+ [Using Contact Attributes](#using-contact-attributes)
+ [User\-Defined Attributes](#user-defined-attributes)
+ [System Attributes for Contact Flows](#system-attributes)
+ [External Attributes](#external-attributes)
+ [Using Contact Attributes to Personalize the Customer Experience](#use-attributes-cust-exp)
+ [Use Amazon Connect Contact Attributes with Other Services](#attribs-external-references)
+ [Using Attributes in the Contact Control Panel](#use-attribs-ccp)
+ [Referencing Contact Attributes](#how-to-reference-attributes)
+ [Using System Metric Attributes](#attrib-system-metrics)
+ [Contact Attributes Available in Amazon Connect](#connect-attrib-list)
+ [System Metrics Attributes](#attribs-system-metrics-table)

In Amazon Connect, a contact is an interaction with a customer in your contact center\. The interaction can be a voice phone call with a human agent, or an automated interaction using an Amazon Lex bot\. Contact attributes in Amazon Connect refer to key\-value pairs of data about a contact\.

Using contact attributes, you can customize and personalize the experience customers have when they interact with your contact center\. Contact attributes let you store customer input or data about a customer, and then use it later in a contact flow\. You can also check the values of contact attributes and use a condition to determine the branching behavior of the contact flow based on the value\.

Contact attributes let you pass data between Amazon Connect and other services, such as Amazon Lex and AWS Lambda\. Contact attributes can be both set and consumed by each service\. For example, you could use a Lambda function to look up customer information, such as their name or order number, and use contact attributes to store the values returned to Amazon Connect\. You could then reference those attributes to include the customer's name in messages using text to speech, or store their order number so they do not have to enter it again\.

## Using Contact Attributes<a name="using-contact-attributes"></a>

When you create a contact flow, you can create user\-defined contact attributes using **Set contact attributes** blocks\. You can then reference them in other parts of a contact flow using any other block that supports dynamic attributes\. For example, you could use a **Check contact attributes** block to compare the value of an attribute to a condition you define, and then route the contact based on the comparison\. You could also retrieve data from external sources, and then create user\-defined attributes from the external data so that you can reference them later in a contact flow, such as the status of an order or an expected shipping date\.

Personalize the customer experience by including the customer's name when you use text to speech text in a **Play prompt** or **Get customer input** block to speak messages to your customer\. Use contact attributes to store input provided by a customer during an interaction with a Amazon Lex bot to enable automated interactions\.

As a best practice, treat attributes and attribute values as case\-sensitive, and always match case in each context where they are used\.

There are three types of contact attributes in Amazon Connect:
+ *User\-defined*—These attributes are created during the execution of a contact flow using **Set contact attributes** blocks\. When you get data from an external source, you can copy key\-value pairs as user\-defined attributes to reference later in a contact flow\. User\-defined attributes can also be created through the Amazon Connect API\.
+ *System*—These are predefined attributes in Amazon Connect\. You can reference system attributes, but you cannot create them\. There are system attributes related to contacts, and system attributes related to metrics\.
+ *External*—These attributes are created via a process external to Amazon Connect, such as when you use an **Invoke AWS Lambda function** block in a contact flow, or integrate with an Amazon Lex bot\.

## User\-Defined Attributes<a name="user-defined-attributes"></a>

User\-defined attributes include all attributes set by using a **Set contact attributes** block in a contact flow\. User\-defined attributes are included in contact trace records \(CTRs\), are available to Lambda functions that are invoked after the **Set contact attributes** block, and are created in the Attributes namespace\. They are also available to applications that integrate with the CCP for screenpop information, and can be referenced in contact flows\.

## System Attributes for Contact Flows<a name="system-attributes"></a>

There are four system attributes related to contacts available in contact flow blocks\.
+ **Customer number**—The phone number of the customer\. The phone number of the customer\. This attribute is included in the CTRs and Lambda input object under CustomerEndpoint\.
+ **Dialed number**—The number that the customer dialed to reach your contact center\. This attribute is included in the CTRs and Lambda input under SystemEndpoint\.
+ **Customer callback number**—The number that the system uses to call the customer back, either for the **Transfer to callback** queue functionality, or for an agent dialing from the CCP\. The default value is the number the customer used to call your contact center, but can be overwritten with the **Set callback number** block\. This attribute is not included in CTRs, and not accessible in Lambda input\. You can copy the attribute to a user\-defined attribute with the **Set contact attribute** block, which is included in CTRs\. You can also pass this attribute as a Lambda input parameter in an **Invoke AWS Lambda function** block, which is not included in CTRs\.
+ **Stored customer input**—The attribute values created from the most recent **Store customer input** block invocation\. This attribute is not included in CTRs, and is not accessible in Lambda input\. You can copy the attribute to a user\-defined attribute with the **Set contact attribute** block, which is included in CTRs\. You can also pass this attribute as a Lambda input parameter in an **Invoke AWS Lambda function** block, which is not included in CTRs\. This attribute value applies only to the most recent invocation of the Lambda function\. It is overwritten with the next invocation of the function\.

## External Attributes<a name="external-attributes"></a>

External attributes are returned as key\-value pairs from the most recent invocation of an **Invoke AWS Lambda function** block\. External attributes are overwritten with each invocation of the Lambda function\. You can access external attributes in contact flows via $\.External\.AttributeName\. For more information about using attributes in Lambda functions, see [Granting Amazon Connect Access to AWS Lambda Functions](http://docs.aws.amazon.com//connect-lambda-functions.html)\.

These attributes are not included in CTRs, not passed to the next Lambda invocation, and not passed to the CCP for screenpop information\. However, they can be passed as Lambda function inputs on an **Invoke AWS Lambda function** block, or copied to user\-defined attributes via the **Set contact attributes** block\. When used in **Set contact attributes** blocks, the attributes that are copied are included in CTRs, and can be used in the CCP\.

## Using Contact Attributes to Personalize the Customer Experience<a name="use-attributes-cust-exp"></a>

Contact attributes in your contact flows can provide a more personalized customer experience\. For example, specify a custom call flow based on comparing an attribute to a value, and then route the call based on the value comparison, such as routing customers to different tiers of support based on their account number\. Or retrieve a customer's name, save the name as an attribute, and then include the name attribute in a text to speech string so that the customer's name is said during the interaction\.

The steps in the following sections describe how to use contact attributes with different blocks in a contact flow\.

### Using a Set Contact Attributes Block<a name="use-set-contact-attrib-block"></a>

Use a **Set contact attributes** block to set a value that is later referenced in a contact flow\. For example, you could create a personalized greeting for customers routed to a queue based on the type of customer account, or define an attribute for a company name or line of business to include in text to speech strings said to a customer\. The **Set contact attributes** block is useful for copying attributes retrieved from external sources to user\-defined attributes\.

**To set a contact attribute with a Set contact attributes block**

1. In Amazon Connect, choose **Routing**, **Contact flows**\.

1. Select an existing contact flow, or create a new one\.

1. Add a **Set contact attributes** block\.

1. Edit the **Set contact attributes** block, and choose **Save text as attribute**\.

1. For the **Destination** key, provide a name for the attribute, such as *Company*\. For the **Value**, use your company name\.

### Capture Customer Input and Store it as an Attribute<a name="capture-cust-input"></a>

You can use an attribute to request a callback number from a customer, store the value of the attribute, and then reference the attribute in a **Set callback number** block to set the number to dial the customer\. You could also use a **Store customer input** block to capture any numeric input from a customer, such as an account or order number\.

**To create an attribute from customer input with a Store customer input block**

1. In Amazon Connect, choose **Routing**, **Contact flows**\.

1. Select an existing contact flow, or create a new one\.

1. Add a **Store customer input** block\.

1. Edit the block, and select **Text to speech \(Ad hoc\)**\.

1. In the **Enter text** box, type a message that is said to customers when they call, such as “Please enter your phone number\.”

1. In the **Customer input** section, select **Phone number**, and then choose the format\. **Local format** is for a number in the same country as the region in which you created your Amazon Connect instance\. **International format/Enforce E\.164** is for numbers to a country other than the country in which you created your instance\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-store-cust-input-phone.png)

1. Add a **Set callback number** block to your contact flow, and connect it to the **Get customer input** block\.

1. Under **Use attributes**, for **Type**, choose **System**\. For **Attribute**, choose **Stored customer input**\. The callback number is set to the number the customer entered when asked to enter their phone number\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-set-callback-number-attrib.png)

### Using Attributes with a Lambda Function<a name="attribs-with-lambda"></a>

Retrieve data from a system your organization uses internally, such as an ordering system or other database with a Lambda function, and store the values as attributes that can then be referenced in a contact flow\.

When the Lambda function returns a response from your internal system, the response is key\-value pairs of data\. You can reference the values returned in the External namespace, for example $\.External\.attributeName\. To use the attributes later in a contact flow, you can copy the key\-value pairs to user\-defined attributes using a **Set contact attributes** block\. You can then define logic to branch your contact based on attribute values by using a **Check contact attributes** block\. Any contact attribute retrieved from a Lambda function is overwritten with the next invocation of a Lambda function\. Make sure you store external attributes if you want to reference them later in a contact flow\.

**To store an external value from a Lambda function as a contact attribute**

1. In Amazon Connect, choose **Routing**, **Contact flows**\.

1. Select an existing contact flow, or create a new one\.

1. Add an **Invoke AWS Lambda function** block\.

1. Add the **Function ARN** to your AWS Lambda function that retrieves customer data from your internal system\.

1. After the **Invoke AWS Lambda function** block, add a **Set contact attributes** block and connect the **Success** branch of the **Invoke AWS Lambda function** block to it\.

1. Edit the **Set contact attributes** block, and select **Use attribute**\.

1. For the **Type**, choose **External**\.

1. For **Destination key**, type a name to use as a reference to the attribute, such as customerName\.

1. For **Source attribute** type the name of the attribute returned from the Lambda function\. The name of the attribute returned from the function will vary depending on your internal system and the funtion you use\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-set-attrib-from-lambda.png)

After this block executes during a contact flow, the value is saved as a user\-defined attribute with the name specified by the **Destination key**, in this case customerName\. It can be accessed in any block that uses dynamic attributes\.

To branch your contact flow based on the value of an external attribute, such as an account number, use a **Check contact attributes** block, and then add a condition to compare the value of the attribute to\. Next, branch the contact flow route based on the condition\.

****

1. In the **Check contact attributes** block, for **Attribute to check** do one of the following:
   + Select **External** and then type the key name returned from the Lambda function\.
**Important**  
Any attribute returned from an AWS Lambda function is overwritten with the next function invocation\. To reference them later in a contact flow, store them as user\-defined attributes\.
   + Select **User defined** and then type the name that you specified as the **Destination key** in the **Set contact attributes** block\.

1. Choose **Add another condition**\.

1. Under **Conditions to check**, choose the comparison type and specify a value to compare to\. A branch is created for each comparison you enter, letting you route the contact based on the conditions specified\. If no condition is matched, the contact takes the **No Match** branch from the block\.

## Use Amazon Connect Contact Attributes with Other Services<a name="attribs-external-references"></a>

You can reference contact attributes set in your Amazon Connect contact flow in other services, such as in an Amazon Lex bot or AWS Lambda function, so that data associated with the customer or the contact can be shared between services for a seamless customer experience\. To use contact attributes to access other resources, set a user\-defined attribute in your contact flow and use the Amazon Resource Name \(ARN\) of the resource you want to access as the value for the attribute\. For example, to use an Amazon Connect prompt in a Lambda function, set a user\-defined attribute to the ARN for the prompt, and then access that attribute from the Lambda function\.

## Using Attributes in the Contact Control Panel<a name="use-attribs-ccp"></a>

Contact attributes also let you capture information and then present that information in a screenpop to an agent in the Contact Control Panel \(CCP\)\. Use contact attributes to customize the agent experience when using the CCP integrated with a customer relationship management \(CRM\) application\. Also use them when integrating Amazon Connect with a custom application using the Amazon Connect Streams API or Amazon Connect API\. You can use all user\-defined attributes, in addition to the customer number and the dialed number, in the CCP using the Amazon Connect Streams JavaScript library\. For more information, see [Amazon Connect Streams API](https://github.com/aws/amazon-connect-streams) or Amazon Connect API\.

When you use the Amazon Connect Streams API, you can access user\-defined attributes by invoking contact\.getAttributes\(\)\. You can access endpoints via contact\.getConnections\(\), where a connection has a getEndpoint\(\) invocation on it\.

To access the attribute directly from a Lambda function, use $\.External\.AttributeName\. If the attribute is stored to a user\-defined attribute from a **Set contact attributes** block, use $\.Attributes\.AttributeName\.

For example, included with your Amazon Connect instance, there is a contact flow named “Sample note for screenpop\.” In this contact flow, a **Set contact attributes** block is used to create an attribute from a text string\. The text, as an attribute, can be passed to the CCP to display a note to an agent\.

## Referencing Contact Attributes<a name="how-to-reference-attributes"></a>

The way you reference contact attributes depends on how they were created and how you are accessing them\. To reference attributes in the same namespace, such as a system attribute, you use the attribute name, or the name you specified as the **Destination key**\. To reference values in a different namespace, such as referencing an external attribute, you specify the JSONPath syntax to the attribute\.

For example, to reference a customer name from a Lambda function lookup, you would use $\.External\.AttributeName, replacing AttributeName with the name of the attribute returned from the Lambda function\. To reference an attribute from an Amazon Lex bot, you use the format $\.Lex\. and then include the part of the Amazon Lex bot to reference, such as $\.Lex\.intentName or $\.Lex\.dialogState\. To reference the customer input to an Amazon Lex bot slot, use $\.Lex\.Slots\.slotName\.

JSONPath is a standardized way to query elements of a JSON object\. JSONPath uses path expressions to navigate elements, nested elements, and arrays in a JSON document\. For more information about JSON, see [Introducing JSON](http://www.json.org/)\.

### Referencing Attributes from a Check Contact Attributes Block<a name="check-contact-attrib-block"></a>

In the **Check contact attributes** block, set the **Attribute to check** to one of the following:
+ **User Defined**—If you choose **User Defined**, in the second field, type the name of the attribute to compare to the condition\. In the following image, the attribute to check is an intent from an Amazon Lex bot, and the conditions to check are input values to the bot to determine the user’s intent\.
+ **External**—If you choose **External**, in the second field type the name of the attribute to compare to the condition\. Define the conditions to check, and then when you save the block, a branch is added for each condition you specify\. Determine how the contact is routed by connecting the branches to other blocks in your contact flow\.
+ **System**—If you choose **System**, specify the system attribute to compare to the condition\.

### Referencing Attributes from a Play Prompt Block<a name="attribs-play-prompt"></a>

To use the values of a contact attribute to personalize a message for a customer, use a **Play prompt** block, and then include references to the stored contact attributes in the text\-to\-speech message\. For example, if you retrieved the customer’s name from a Lambda function, and it returns values from your customer database for FirstName and LastName, you could use these attributes to say the customer’s name in the text\-to\-speech block by including text similar to the following:

Hello $\.External\.FirstName $\.External\.LastName, thank you for calling\.

Alternatively, you could store the attributes returned from the Lambda function using a **Set contact attributes** block, and then reference the user\-defined attribute created in the text to speech string\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-play-prompt-tts-attribs.png)

### Getting Customer Input Using an Amazon Lex Bot<a name="attribs-cust-input-lex-bot"></a>

When you reference attributes in a **Get customer input** block, and choose Amazon Lex as the method of collecting the input, the attribute values are retrieved and stored from the output from the customer interaction with the Amazon Lex bot\. You can use an attribute for each intent, dialog state, or slot used in the Amazon Lex bot\. To reference these attributes in a contact flow, use the following format:

$\.Lex\.LexAttributeName, such as $\.Lex\.DialogState or $\.Lex\.IntentName

You can reference the value of a specific slot in the Amazon Lex bot by using the following format:

$\.Lex\.Slots\.slotName where slotName is the name of the slot to reference in the Amazon Lex bot\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-get-cust-input-lex-attribs.png)

## Using System Metric Attributes<a name="attrib-system-metrics"></a>

Amazon Connect includes system metric attributes that can help you define routing conditions in your contact flows based on real\-time metrics about the queues and agents in your contact center\. When you include a **Get metrics** block in your contact flow, metrics are retrieved for the current working queue, or other queue that you specify\.

You can reference the metric attributes returned to determine the optimal route for a contact by checking current queue metrics, such as the number of contacts currently in a queue, the number of available agents in a queue, and the length of time the oldest contact has been in a queue\. You could even get metrics for multiple queues and use a **Set contact attributes** block to store the metric attributes\. You could then compare queue metric attributes using a **Check contact attributes** block, and route the contact to the queue with the fewest calls in it, or to a callback if all queues are busy\. To learn more about the metric attributes available, see [System Metrics Attributes](#attribs-system-metrics-table)\.

**To use system metrics attributes in a contact flow**

1. In Amazon Connect, choose **Routing**, **Contact flows**\.

1. Select an existing contact flow, or create a new one\.

1. Add a **Get metrics** block to the contact flow\.

1. Optionally, to specify a queue select the **Set queue** check box and do one of the following:
   + Select the queue to retrieve metrics for from the drop\-down list\.
   + Select **Use attribute**, and the select the attribute to use\.

   If you do not select a queue, metrics are retrieved for the current working queue\.

1. Add a **Check contact attributes** block and connect the **Success** branch of the **Get metrics** block to it\.

1. In the **Check contact attributes** block, specify the metric attribute to use, and then add conditions to check the value against like any other attribute\.

1. Add additional blocks to the contact flow and route the contact based on the result of the conditions checked\.

## Contact Attributes Available in Amazon Connect<a name="connect-attrib-list"></a>

The following sections describes the contact attributes available in Amazon Connect\.

### Contact Flow System Attributes<a name="attribs-system-table"></a>


| Attribute | Description | Type | 
| --- | --- | --- | 
| Customer number | The customer’s phone number\.  | System | 
| Dialed number |  The number the customer dialed to call your contact center\. | System | 
| Customer callback number | The number to dial to call back the customer\. | System | 
| Stored customer input | An attribute created from the most recent invocation of a **Store customer input ** block\. | System | 

### External Contact Attributes<a name="attribs-lambda-table"></a>

The following table describes the external attributes from a Lambda function\.


| Attribute | Description | Type | 
| --- | --- | --- | 
| ContactId  | The unique identifier for the contact\. | External | 
| OriginalContactId | The unique identifier for the contact created for the first interaction the customer had with your contact center\. Use the OriginalContactId to trace contacts between contact flows\. | External | 
| PreviousContactId | The unique identifier for the contact before it was transferred\. You can use the PreviousContactId to trace contacts between contact flows\. | External | 
| Channel  | The method of contact\. Currently, only VOICE is supported in Amazon Connect\. | External | 
| InstanceARN | The ARN for your Amazon Connect instance\. | External | 
| InitiationMethod | How the contact was initiated\. Valid values include: INBOUND, OUTBOUND, TRANSFER, CALLBACK, or API\. | External | 
| SystemEndpoint\.Address | The number the customer dialed to reach your contact center\. | External | 
| CustomerEndpoint\.Address | The customer’s phone number\. | External | 
| Queue\.Name | The name of the queue to route the contact to\. | External | 
| Queue\.ARN  | The ARN for the queue\. | External | 
| TextToSpeechVoiceId | The name of the voice to use, such as Joanna, for text\-to\-speech phrases in a contact flow\. | External | 

### Contact Attributes from Amazon Lex<a name="attribs-lex-table"></a>

The following table lists the attributes available from Amazon Lex bots\.


| Attribute | Description | Type | 
| --- | --- | --- | 
| dialogState  | The last dialog state returned from an Amazon Lex bot\. The value is 'Fulfilled' if an Intent was returned to the contact flow\. | External | 
| intentName  | The user intent returned by Amazon Lex\. | External | 
| Slots  | Map of intent slots \(key/value pairs\) Amazon Lex detected from the user input during the interaction\. | External | 
| sessionAttribute | Map of key\-value pairs representing the session\-specific context information\. | External | 

## System Metrics Attributes<a name="attribs-system-metrics-table"></a>

The metrics attributes in the following table are returned when you use the **Get metrics** block to retrieve metrics for a queue\. If there is no current activity in your contact center, null values are returned for these attributes\.


| Attribute | Description | Type | 
| --- | --- | --- | 
| Queue\.Name | The name of the queue\. | System | 
| Queue\.ARN | The ARN for the queue\. | System | 
| TextToSpeechVoiceId | The name of the voice to use for text\-to\-speech\. | System | 
| ContactId | The unique identifier of the contact\. | System | 
| InitialContactId | The unique identifier for the first contact a customer had with your contact center\. Use the InitialContactId to track contacts between contact flows\. | System | 
| PreviousContactId | The unique identifier for the contact before it was transferred\. Use the PreviousContactId to trace contacts between contact flows\. | System | 
| Channel | The method of contact\. Currently, only VOICE is supported in Amazon Connect\. | System | 
| InstanceARN | The ARN for your Amazon Connect instance\. | System | 
| InitiationMethod | How the contact was initiated\. Valid values include: INBOUND, OUTBOUND, TRANSFER, or CALLBACK\. | System | 
| SystemEndpoint\.Type | The type of endpoint for a contact\. Currently only TELEPHONE\_NUMBER is supported\. | System | 
| SystemEndpoint\.Address | The value for the system endpoint\. Currently only a telephone number is supported\. | System | 
| CustomerEndpoint\.Type | The type of endpoint for the customer\. Currently only TELEPHONE\_NUMBER is supported\. | System | 
| CustomerEndpoint\.Address | The value for the customer endpoint\. Currently only a telephone number is supported\. | System | 
| Queue\.OutboundCallerId | The outbound caller ID number defined for the queue\. This can be useful for reverting the caller ID after setting a custom caller ID\. | System | 
| Agent\.UserName | The user name an agent uses to log in to Amazon Connect\. | System | 
| Agent\.FirstName | The agent’s first name as entered in their Amazon Connect user account\.  | System | 
| Agent\.LastName |  The agent’s last name as entered in their Amazon Connect user account\. | System | 
| Agent\.ARN | The ARN of the agent\. | System | 
| Metrics\.Queue\.Name | The name of the queue for which metrics were retrieved\. | System | 
| Metrics\.Queue\.ARN | The ARN of the queue for which metrics were retrieved\. | System | 
| Metrics\.Queue\.Size | The number of contacts currently in the queue\. | System | 
| Metrics\.Queue\.OldestContactAge | For the contact that has been in the queue the longest, the length of time that the contact has been in the queue, in seconds\. | System | 
| Metrics\.Agents\.Online\.Count | Number of agents currently online \(in any state other than offline\)\. | System | 
| Metrics\.Agents\.Available\.Count | Number of agents whose state is set to Available\. | System | 
| Metrics\.Agents\.Staffed\.Count | Number of agents currently staffed, which is agents in Available, ACW, or Busy states\. | System | 
| Metrics\.Agents\.AfterContactWork\.Count | Number of agents currently in ACW state\. | System | 
| Metrics\.Agents\.Busy\.Count | Number of agents currently active on a contact\. | System | 
| Metrics\.Agents\.Missed\.Count | Number of agents in Missed state, which is the state an agent enters after a missed call\. | System | 
| Metrics\.Agents\.NonProductive\.Count | Number of agents in a non\-productive state\. | System | 