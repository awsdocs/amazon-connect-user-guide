# Creating Contact Search Reports<a name="contact-search"></a>

Contact trace records \(CTR\) are the documents Amazon Connect maintains for each contact in the system\. It summarizes important events and statistics about each call, and serves as the basis for historical and near\-real\-time statistics calculations\.

The **CTR search** page contains filters with which to search through contact history\. The results contain information about the call, as well as hosting the controls to enable live listening or call recording downloads\. You can also view detailed information about each call, such as the direction of the call, queue time, recording status, and customer phone number\.

Contact search records have a 14\-day time\-range limit\. It is not possible to share or save **Contact search** reports\. However you can download a CSV copy of generated reports\. The following default filters are available:

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

+ **Additional fields**—The following additional filters are available:

  + **Routing Profile**—The routing profile of the agent who handled the call\.

  + **Agent interaction duration**—The total time the agent and customer were connected, excluding hold periods\. 

  + **Original contact ID**—For transfers, this is the first customer media leg that arrived in the system\.

  + **Connected to agent timestamp**—The date and time at which the customer was connected to an agent\.

  + **Number of agent join attempts**—The total number of times that the system attempted to connect the customer with an agent, including the last attempt if the call was handled\.

  + **Previous contact ID**—For transfers, the customer leg that preceded the current call leg\.

  + **ACW start timestamp**—The time when the agent began after call work\.

  + **Number of holds**—The number of times that this call was put on hold\. The initial queuing period does not count as a hold\.

  + **Next contact ID**—The identifier of the next contact in an interaction sequence\. Not set for single\-contact interactions, or for the last contact\.

  + **ACW end timestamp**—The time at which the agent completed after call work\.

  + **Is transferred out**—Indicates if the call was transferred by the agent who handled this call\.

**To generate a contact search record**

1. Choose **Metrics and quality**, **Contact search**\.

1. Adjust the values for **Filters** as needed\.

1. Choose **Additional fields**, select additional parameters, and choose **Apply**\.

1. Choose **Search**, **Download CSV**\.

## Contact Search Definitions<a name="contactdetailrecords-definitions"></a>

The table of results contains a row for each call that matches the filters\.

The following are definitions for the default fields:

+ **Contact ID**—The customer call leg identifier\. Choose the hyperlink to view detailed information about this customer’s contact history\.

+ **Initiation Timestamp**—When the call arrived in the system\.

+ **Phone Number**—The number that the customer dialed \(inbound call\)\.

+ **Queue**—Queue to which the call was assigned\.

+ **Agent**—Login ID of the agent who handled the call \(if applicable\)\.

+ **Recording**—Controls for playing back or downloading the call recording\. This is available only if the call was handled by an agent\.

+ **Customer Number**—The customer's phone number\. For outbound calls, this is the number that the agent dialed\.

+ **Disconnect Timestamp**—When the call ended\. After call work may extend beyond this time\.

To view detailed information about each call, choose **Contact ID**\. This is a non\-editable, detailed breakdown of the entire customer/agent interaction\.