# Creating a Customer Contact Flow<a name="routing"></a>

This section describes the steps necessary to enable customer contact flows in your Amazon Connect instance\.

**Topics**
+ [Claiming Phone Numbers](#phone-numbers)
+ [Creating Hours of Operation](#hoursoperation)
+ [Working with Queues](#queues)
+ [Creating Prompts](#prompts)
+ [Creating Quick Connects](#quickconnect)

## Claiming Phone Numbers<a name="phone-numbers"></a>

To place or receive calls in your instance, you need to claim a phone number\. If you did not claim a number when you created the instance, follow these steps to claim one now\. You can claim numbers from the Amazon Connect Dashboard or from the **Manage phone numbers** page\.

**To claim a number for your contact center**

1. Choose **Routing**, **Phone numbers**\.

1. Choose **Claim a number** in the top\-right corner of the screen\. You can choose a **Toll free** or a **DID \(Direct Inward Dialing\)** number\.
**Note**  
If you want to select a number from a country, but there are no numbers displayed for that country when you select it, you can request additional numbers for that country using the [Amazon Connect service limits increase form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-connect)\.  
If you want to keep a phone number you already have, you can port the phone number and use it with Amazon Connect\. To learn more, see [Port Your Current Phone Number](https://docs.aws.amazon.com/connect/latest/adminguide//gettingstarted.html#numberporting)\.

1. Enter a description for the number and, if required, attach it to a contact flow in **Contact flow / IVR**\.

1. Choose **Save**\.

You can repeat this process until you have claimed all your required numbers\.

You can add or edit descriptions, assign queues, and attach contact flows to the numbers\. You can also define a contact flows that includes prompts to support customer self\-service\.

**To associate a phone number with a contact flow**

1. Choose **Routing**, **Phone numbers**\.

1. You can search for a specific number, filter your search by queue, or select a number from the list provided \(if applicable\)\.

1. Select the number to edit, expand **Contact flow / IVR**, and select the contact flow\.

1. Choose **Save**\.

There is a service limit of 10 phone numbers per Amazon Connect instance\. If you reach your limit, but want a different phone number, you can release one of previously claimed numbers\. To do this, choose **Release**, **Release**\. You cannot claim the same number after releasing it\. If you need more than 10 phone numbers, you can request a service limit increase using the [Amazon Connect service limits increase form](https://console.aws.amazon.com/support/home#/case/create?issueType=service-limit-increase&limitType=service-code-connect)\.

### Making International Calls<a name="international_calls"></a>

Amazon Connect requires phone numbers in [ E\.164](https://www.itu.int/rec/T-REC-E.164/en) format\. E\.164 is an international public telecommunication numbering plan defined by the International Telecommunication Union \(ITU\)\. Using phone numbers in E\.164 format ensures that numbers are interpreted consistently when placing calls between countries, and when phone numbers are passed between software applications and telephony services\.

When you place calls from the CCP using Amazon Connect the CCP provides the correct formatting for numbers automatically\.

E\.164 defines a general format for international telephone numbers\. Numbers are limited to a maximum of 15 digits, excluding the international call prefix\. The presentation of a number is usually prefixed with the plus sign \(\+\), indicating that the number includes the country calling code\. When dialing, the number must typically be prefixed with the appropriate international call prefix \(in place of the plus sign\), which is a trunk code to reach an international circuit from within the country of call origination\. Phone numbers that are not formatted in E\.164 may work, but it depends on the phone or handset that is being used as well as the carrier from which the call is being originated\.

To express a US phone number to E\.164 format, add the '\+' prefix and the country code \(1\) in front of the number\. In the UK and many other countries internationally, local dialing requires the addition of a 0 in front of the subscriber number\. However, to use E\.164 formatting, this 0 must be removed\. A number such as 020 718 xxxxx in the UK would be formatted as \+44 20 718 xxxxx\.

## Creating Hours of Operation<a name="hoursoperation"></a>

Hours of operation define when a queue is available, and may be referenced in contact flows\. Hours of operation are a required component when setting up queues, and must be completed first\.

**To add hours of operation in the console**

1. Choose **Routing**, **Hours of operation**\.

1. To create a template, choose **Add new hours** and enter a name and a description\.

1. For **Time zone**, select a value\.

1. For **Add new**, set new hours\.

1. Choose **Save**\.

## Working with Queues<a name="queues"></a>

A queue is 'waiting area' that holds contacts to be answered by agents\. You can use a single queue to handle all incoming contacts, or you can set up queues mapped to agents with specific skill sets\. 

Contacts are routed through your contact center based on the routing logic you define in your contact flows\. You can also use routing profiles to manage how agents are allocated to queues, such as routing specific types of contacts to agents with specific skill sets\. If no agent with the required skill set is available, the contact is placed in the queue you define in the contact flow\.

Calls in a queue are automatically prioritized and forwarded to the next available agent\. Customers are placed on hold if there are no available agents\. The order in which they are serviced is determined by their time in queue, on a first\-come, first\-served basis\. If multiple agents are available, the call is routed to the agent who has been in the **Available** status for the longest time\.

A routing profile may assign a priority to one queue over another, but the priority within the queue is always set by the order the contact was added to the queue\.

Use the metrics and reporting features of Amazon Connect to monitor queue performance and wait times in your contact center to optimize agent efficiency and reduce customer hold times\. Make sure to plan for peak busy times and how additional calls are handled when your contact center is at full call capacity\. To learn more about queue metrics, see [Amazon Connect Metrics and Reports](connect-metrics.md)\. To learn more about using queue metric attributes in contact flows, see [Using System Metric Attributes](contact-attributes.md#attrib-system-metrics)\.

Queue metrics can be monitored and reviewed using both real\-time and historical metrics\. Metrics include **Service Level**, **Average Handle Time**, **Average Abandon Time**, and **Average Hold Time**\.

**To create a new queue**

1. Choose **Routing**, **Queues**, **Add new queue**\.

1. Add the appropriate information about your queue and choose **Add new queue**\.

**Important**  
When you create a queue, you can specify an **Outbound caller ID name** and **Outbound caller ID number**\. You can also provide a phone number in a **Set callback number** block in a contact flow\. The callback name and number is sent as the origination party when Amazon Connect initiates the call to the destination\. However, the information displayed to the person called may not always match the name or number set during call initiation\. In some cases, the callback name is provided by the carrier of the person you are calling\. The information may not be up\-to\-date with that carrier, or the number may get passed differently between systems due to hardware or configuration differences\. If this is the case, the person that you call may not see the phone number, or may see the name of a previously registered owner of the number, instead of the name of the registered person from your organization\.

When you create a queue, it is automatically active and can be assigned to a routing profile\. Users with the proper permissions can deactivate the queue, which puts it in an offline mode and makes it unavailable to assign to a routing profile\.

**To disable an active queue**

1. Choose **Routing**, **Queues**\.

1. Hover over the name of the queue to edit and choose the power icon\.

1. Choose **Disable**\.

To reactivate a queue, follow the same steps as above\.

**To edit a queue**

1. Choose **Routing**, **Queues**, and select the queue to edit\.

1. Edit the queue details as required\.

1. Choose **Save**\.

## Creating Prompts<a name="prompts"></a>

Prompts are audio files played in call flows\. Only 8 KHz \.wav files that are less than 50 MB are supported for prompts\. You can upload a pre\-recorded \.wav file to use for your prompt, or record one in the web application\. Prompts and routing policies should be aligned with each other to ensure a smooth call flow for customers\.

**To create a prompt**

1. Choose **Routing**, **Prompts**\.

1. On the **Manage voice prompts** screen, choose **\+Create new prompt**\.

1. You can choose the following actions:
   + **Upload**—Choose the file to upload\.
   + **Record**—Choose the red circle to begin recording\. Use the red square to stop\. You can choose **Crop** to cut the recorded prompt or **Discard** to record a new prompt\.

1. For **Step 2: Input basic information**, enter the name of the file, and then choose **Create**\.

**To manage recorded prompts**

1. Choose **Routing**, **Prompts**\.

1. On the **Manage voice prompts** screen, select the appropriate prompt\.

1. You can choose **Play**, **Download**, **Edit**, or **Delete**\.

1. Choose **Save**\.

## Creating Quick Connects<a name="quickconnect"></a>

Calls can be transferred to an agent, a queue, or an external number\.
+ **External**—Calls are transferred to an external number \(such as an on\-call pager\)\. 
+ **Agent**—Calls are transferred to a specific agent as part of a contact flow\.
+ **Queue**—Calls are transferred to a queue as part of a contact flow\.

**To add a quick connect**

1. Choose **Routing**, **Quick connects**, **Add a new destination**\.

1. Enter a name for the item, and select a type, destination, contact flow \(if applicable\), and description\.
**Important**  
A description is required when you create a quick connect\. An error is returned if you do not add a description\.

1. To add more rows, choose **Add a new destination**\.

1. Choose **Save**\.

To see your quick connects in the contact list in CCP, add them to **Queues**\. Agent and queue quick connects only appear when an agent transfers a call\.
