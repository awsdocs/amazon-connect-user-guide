# Configuring Interactive Voice Response Workflows<a name="routing"></a>

You can ensure effective customer contact handling with interactive voice response \(IVR\) workflows, using queues, contact flows, and quick connects\. These workflows provide a seamless customer experience, funneling contacts to the correct agents, and ensuring SLA adherence\.

## Claiming Phone Numbers<a name="phone-numbers"></a>

You can claim a phone number when you first create an instance, from the **Dashboard**, or you can claim one from the **Manage phone numbers** screen\. You can also release a number that you no longer use\.

**Note**  
There is a limit of 10 numbers per contact center\. If you reach your limit and no longer need a number, you can release it to make space for a new number\. To do this, choose **Release**, **Release**\. You cannot claim the same number again\.

**To claim a number for your contact center**

1. Choose **Routing**, **Phone numbers**\.

1. Choose **Claim a number** in the top\-right corner of the screen\. You can choose a **Toll free** or a **DID \(Direct Inward Dialing\)** number\.
**Note**  
You cannot enter a number of your choice and you can only choose one number across both types\.

1. Enter a description for the number and, if required, attach it to a contact flow in **Contact flow / IVR**\.

1. Choose **Save**\.

You can repeat this process until you have claimed all your required numbers\.

You can add or edit descriptions, assign queues, and attach call flows to the numbers\. You can also define an IVR workflow, which includes prompts, to support customer self\-service\. 

**To associate a phone number with a contact flow**

1. Choose **Routing**, **Phone numbers**\.

1. You can search for a specific number, filter your search by queue, or select a number from the list provided \(if applicable\)\.

1. Select the number to edit, expand **Contact flow / IVR**, and select the contact flow\.

1. Choose **Save**\.

### Making International Calls<a name="international_calls"></a>

Amazon Connect uses the E\.164 format for international dialing\. This formatting is pre\-configured in the CCP\.

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

## Creating Hours of Operation<a name="hoursoperation"></a>

Hours of operation define when a queue is available, and may be referenced in contact flows\. Hours of operation are a required component when setting up queues, and must be completed first\.

**To add hours of operation in the console**

1. Choose **Routing**, **Hours of operation**\.

1. To create a template, choose **Add new hours** and enter a name and a description\.

1. For **Time zone**, select a value\.

1. For **Add new**, set new hours\.

1. Choose **Save**\.

## Managing Queues<a name="queues"></a>

A queue is list of incoming contacts to be serviced by agents\. You can use a single queue to handle all incoming contacts, or you can set up queues mapped to agents with specific skill sets\.

Amazon Connect uses an automatic call distributor \(ACD\) to distribute incoming contacts to specific resources or agents within the call center, based on the selections made within the IVR\. If an agent with a skill set matching the selection is not available the customer is placed in a pre\-defined queue\.

Calls in a queue are automatically prioritized and forwarded to the next available agent\. Customers are placed on hold if there are no available agents\. The order in which they are serviced is determined by their time in queue, on a first\-come, first\-served basis\. If multiple resources are available, the call is routed to the agent who has had the **Available** status for the longest time\.

**Note**  
Routing profiles may create an exception where one queue takes priority over another, but the priority within the queue is always set by the order the contact was received\. For more information, see [Configuring Interactive Voice Response Workflows](#routing)\.

Accurate queue management and configuration ensures that an accurate spread of resources, and minimizes customer hold time\. It also ensures that resources can be effectively rerouted during busy periods\. You can have unlimited concurrent active queues\.

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