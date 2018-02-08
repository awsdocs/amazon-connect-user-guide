# Understanding Historical Metrics Grouping<a name="metrics-grouping"></a>

Historical metric reports are grouped into **Queues**, **Agents**, and **Phone numbers** templates, which are pre\-populated with basic filters to fit the report type\. Within each of the reporting template groups, additional filters and metrics can be added to the reports\. 

## Creating Reports Using Groupings<a name="generating-reports"></a>

Groups can be combined or analyzed individually\. The following procedures describe how to group by hierarchy levels with additional metrics for hold time and occupancy, generate a phone numbers report with default groupings and additional filters for service levels per agent, and generate an agent activity audit\.

**To create a grouped contact queue report**

1. Choose **Metrics and Quality**, **Historical metrics**\.

1. Select the arrow next to **Queues** and choose **Contact metrics**\.

1. To open the **Table settings** menu, select the cog icon\.

1. Choose **Groupings**, the **\+** sign, and **Metrics**\.

1. For **Hold time** and **Occupancy**, select the metrics options\.

1. Choose **Apply**\.

**To create a phone numbers report with default groupings and additional filters for service levels per agent**

1. Choose **Metrics and quality**, **Historical metrics**, **Phone numbers**\.

1. To open the **Table settings** menu, select the cog icon\.

1. Choose **Groupings** and drag the **Agent** label to the **Selected groupings** column\.

1. Choose **Metrics**\.

1. Select the additional service\-level metrics options from the list provided\.

1. Choose **Save**\.

**To generate an agent activity audit**

Agent activity audits provide an overview of an agent's activity throughout their shift\. This includes their status changes, and data linked to call status listings\. Agent activity audit reports apply to a single day's activity only\. You can search for activity up to two months old\.

1. Choose **Metrics and Quality**, **Historical metrics**\.

1. Choose **Agents** and **Agent activity audit**\.

1. Enter the agent's login and choose **Generate Report**\.
**Note**  
Enter the exact login; partial and wildcard searches are not supported\.

1. To edit the report, choose the **\+** in the top left corner of the table\. 

1. To save a copy of the report to your computer, choose **Download CSV report**\.

To schedule a report to run at a specific time, choose **Schedule** from the drop\-down menu and enter a name for your report\. If this is a new report, publish it to your organization first\. Choose **New Schedule** and edit the **Recurrence** and **Delivery Options** tabs\.

Choose a prefix for the report to make it easy to locate and choose **Create**\.

## Historical Metrics Definitions<a name="historicalmetrics-definitions"></a>

Historical metrics are defined by groups\. Each group has pre\-selected metrics that are relevant to that group\. Additional metrics per group can be selected\.

Metrics are divided into **Contact metrics** and **Agent metrics**\. Only one option can be selected at a time and relevant metrics are pre\-selected per view\. Additional metrics per view can be selected\.

The definitions below are the complete list of available metrics across all the historical metrics groups and both views\.

+ **Agent idle time**—Sum of time that an agent spent in a productive state, but not handling contacts\.

+ **Average customer hold time**—Average time that customers spent on hold, divided by the number of calls taken\.

+ **Average agent interaction time**—Average amount of time that agents and customers interacted on contacts\.

+ **After contact work time**—Sum of time spent in **After contact work**\.

+ **Agent on contact time**—Sum of time that an agent spent with active contacts\.

+ **Nonproductive time**—Sum of time spent in a nonproductive state, excluding **Error** and **Offline**\.

+ **Average after contact work time**—Average time that an agent spent in **After contact work time**\. 

+ **Average handle time**—Average of **Contact handle time**\.

+ **Average queue abandon time**—Average amount of time that customers spent in a queue before abandoning the call\.

+ **Average agent interaction and customer hold time**—Average of the sum of agent interaction and customer hold time\.

+ **Average agent interaction time**—Average amount of time that agents and customers interacted on contacts\.

+ **Average outbound agent interaction time**—Average of the time that agents interacted with customers on outbound calls\.

+ **Average outbound after contact work time**—Average time that agents spent in **After contact work time** for outbound contacts\.

+ **Contacts abandoned**—Number of contacts when the customer disconnected while in queue\.

+ **Contacts abandoned in x seconds**—Count of contacts when the customer disconnected while in the queue for x number of seconds \(ranges 15–600 seconds\)\.

+ **Contacts agent hung up first**—Count of contacts when the agent disconnected before the customer\.

+ **Contacts consulted**—Count of contacts when an agent consulted with a third party\.

+ **Contacts handled**—Count of contacts handled by an agent\.

+ **Contacts handled incoming**—Count of incoming contacts handled by an agent\.

+ **Contacts handled outbound**—Count of outbound contacts handled by an agent\.

+ **Contacts hold customer disconnect**—Count of contacts disconnected by the customer while the customer was on hold\.

+ **Contacts put on hold**—Count of contacts put on hold by an agent at least one time\.

+ **Contacts hold agent disconnect**—Count of contacts disconnected by the agent while the customer was on hold\.

+ **Contacts hold disconnect**—Count of contacts disconnected while the customer was on hold\.

+ **Contacts joined in x seconds**—Count of contacts that were answered by an agent within x number of seconds \(ranges 15–600 seconds\)\.

+ **Contacts queued**—Count of contacts placed into a queue\.

+ **Contacts transferred in**—Count of contacts transferred to a queue\.

+ **Contacts transferred out**—Count of contacts transferred out of a queue\.

+ **Error status time**—Sum of time that an agent spent in the **Error** status\.

+ **Customer hold time**—Sum of the time that customers spent on hold\. This value does not include queue time\.

+ **Agent answer rate**—Percentage of contacts routed to an agent that were successfully answered\.

+ **Maximum queued time**—The longest amount of time that a customer spent in a queue\.

+ **Contacts missed**—Count of the number of contacts that agents did not answer successfully\. A single contact can be missed multiple times, but eventually answered successfully\.

+ **Contact flow time**—Sum of the time that customers spent in contact flows\.

+ **Transfer out time**—Sum of the time spent after a customer was transferred out by an IVR or agent\.

+ **Contact handle time**—Sum of time that an agent spent on a call, including hold time and **After contact work time**\.

+ **Occupancy**—Agent Handle Time/\(Agent Handle Time \+ Agent Idle Time\)\.

+ **Service level x seconds**—Percentage of contacts answered within x number of seconds \(ranges 15–600 seconds\)\.

+ **Online time**—Sum of the time that an agent spent in states other than **Offline**\.

+ **Agent interaction and hold time**—Sum of the sums of agent interaction and customer hold time\.

+ **Agent interaction time**—Sum of the time that agents interacted with customers\.