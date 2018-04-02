# Creating Contact Search Reports<a name="contact-search"></a>

Contact trace records \(CTR\) are the documents Amazon Connect maintains for each contact in the system\. It summarizes important events and statistics about each call, and serves as the basis for historical and near\-real\-time statistics calculations\.

The **Contact search** page contains filters with which to search through contact history\. The results contain information about the call, as well as hosting the controls to enable live listening or call recording downloads\. You can also view detailed information about each call, such as the direction of the call, queue time, recording status, and customer phone number\.

**To generate a contact search report**

1. Choose **Metrics and quality**, **Contact search**\.

1. Adjust the values for **Filters** as needed\.

1. Choose **Additional fields**, select any additional fields to include in the report, then choose **Apply**\.

1. Choose **Search** to generate the report\. After the report is generated, choose **Download CSV** to download the report to your computer as a CSV file\.

Contact search records have a 14\-day time\-range limit\. It is not possible to share or save **Contact search** reports\. However, you can download a CSV copy of generated reports\. The following default filters are available:
+ **Start date**—Calls connected no earlier than this date\.
+ **End date**—Calls disconnected no later than this date\.
+ **Time zone**—The time zone used to calculate midnight for the start and end dates\. The default setting is **UTC**\.
+ **Initiation method**—Indicates how the contact was initiated\.
+ **Phone number**—The phone number that the customer called\.
+ **Queue**—The skill or queue of the call\.
+ **Agent login**—Finds calls for a specific agent, identified by the agent login\. This search provides exact results\.
+ **Minimum talking seconds**—The minimum number of seconds of talk time between the customer and agent\.
+ **Maximum talking seconds**—The maximum number of seconds of talk time between the customer and agent\.
+ **Customer phone number**—The customer's phone number\.
+ **Contact ID**—An identifier for a contact\. Specify a contact ID if you want to see results only for a specific contact\.

**Additional fields**—The following additional filters are available:
+ **Agent Name**—The agent's name displayed as Last name, First name\.
+ **Agent First Name**—The agent's first name\.
+ **Agent Last Name**—The agent's last name\.
+ ****—
+ **Routing Profile**—The routing profile of the agent who handled the call\.
+ **Connected to agent timestamp**—The date and time at which the customer was connected to an agent\.
+ **ACW start timestamp**—The time at which the agent began after call work \(ACW\)\.
+ **ACW end timestamp**—The time at which the agent completed after call work\.
+ **Agent interaction duration**—The total time the agent and customer were connected, excluding hold periods\. 
+ **Number of agent connection attempts**—The total number of times that the system attempted to connect the customer with an agent, including the last attempt if the call was handled\.
+ **Number of holds**—The number of times that this call was put on hold\. The initial queuing period does not count as a hold\.
+ **Is transferred out**—Indicates if the call was transferred by the agent who handled this call\.
+ **Initial contact ID**—For transfers, this is the first customer media leg that arrived in the system\.
+ **Previous contact ID**—For transfers, the customer leg that preceded the current call leg\.
+ **Next contact ID**—The identifier of the next contact in an interaction sequence\. Not set for single\-contact interactions, or for the last contact in an interaction\.

## Contact Search Report Field Definitions<a name="contactdetailrecords-definitions"></a>

The contact search report is displayed as a table, with a row for each call that matches the specified filters\.

The following definitions describe the fields, or columns, displayed in the report:
+ **Contact ID**—The identifier for the contact associated with the record\. Choose the link to view detailed information about this contact\.
+ **Initiation Timestamp**—When the call arrived in the system\.
+ **Phone Number**—The number that the customer dialed \(inbound call\)\.
+ **Queue**—Queue to which the call was assigned\.
+ **Agent**—Login ID of the agent who handled the call \(if applicable\)\.
+ **Recording**—Controls for playing back or downloading the call recording\. This is available only if the call was handled by an agent\.
+ **Customer Number**—The customer's phone number\. For outbound calls, this is the number that the agent dialed\.
+ **Disconnect Timestamp**—When the call ended\. After call work may extend beyond this time\.

To view detailed information about each call, choose **Contact ID**\. This is a non\-editable, detailed breakdown of the entire customer/agent interaction\.