# Generating Real\-Time Metrics<a name="real-time-metrics"></a>

Real\-time metric reports are grouped into **Queues**, **Agents**, and **Routing profiles** templates\. Within each of the reporting template groups, more filters and metrics can be added to the reports\.

When you select a report template, it's added to the real\-time metrics table and updates automatically\. You can select more report templates by choosing **New table** and selecting a new template\. This template is added to the page and doesn't replace the previous report\. You can also have multiple instances of the same report template running at the same time\. They don't overwrite each other; changing the filters and metric settings on one table does not affect the second instance of that table\.

## Real\-Time Metrics Definitions<a name="realtimemetrics-definitions"></a>

Real\-time metrics are grouped by **Agents**, **Queues**, and **Routing profiles**\. The groups share a common list of metrics to describe activity in each group\.

Agent
+ **Online**—Count of agents in a status other than **Offline**\.
+ **On call**—Count of agents active on a contact\.
+ **Aux**—Count of agents in non\-productive statuses\.
+ **After contact work \(ACW\)**—Count of agents in after\-contact work\.
+ **Error**—Count of agents in the **Error** status\.
+ **Available**—Count of agents available for contacts\.
+ **Staffed**—Count of agents **Available**, **On call**, or in **ACW**\.

Phone
+ **Active**—**1** if the agent is active on a contact; otherwise, **0**\.
+ **Contact state**—Status of the contact last handled or being handled by an agent\.
+ **Availability**—**1** if the agent is available to handle a contact; otherwise, **0**\.
+ **Queue**—Name of the queue associated with the contact being handled\.

Performance
+ **In queue**—Count of customers waiting in the queue\.
+ **Oldest**—Age of the contact that has been in the queue the longest\.
+ **Scheduled**—Count of customers scheduled for callback\.
+ **Handled**—Count of contacts handled by an agent\.
+ **Abandoned**—Count of customers that disconnected while in queue\.
+ **Average handle time \(AHT\)**—The average time that an agent takes to handle a call from start to finish\.
+ **SL x**—Number of contacts that were in the queue for under x seconds \(range 15–600\)\.
+ **Agent hung up first**—Count of contacts when the agent disconnected before the customer\.
+ **Handled in**—Total number of incoming contacts handled by an agent\.
+ **Handled out**—Total number of outgoing contacts handled by an agent\.
+ **Hold abandons**—Count of contacts disconnected while the customer was on hold\.
+ **Consult**—Count of contacts when an agent consulted with a third party\.
+ **Max queued**—Maximum number of contacts queued in the reporting interval\. This includes abandoned contacts and contacts queued before being joined with an agent\.
+ **Missed**—Count of the number of contacts that agents did not answer successfully\. A single contact can be missed multiple times, but ultimately successfully answered\.
+ **Avg abandon time**—The average amount of time that contacts spent in a queue before abandoning the call\.
+ **Avg answer time**—The average amount of time that contacts spent in the queue before being connected to an agent\. Anything before the time that the contact is put into the queue is not included\.
+ **Avg hold time**—The average amount of time that customers spent on hold\.
+ **Avg interaction time**—The average amount of time that agents and customers interacted on contacts\.
+ **Avg interaction and hold time**—The average of the sum of agent interaction and customer hold time\.
+ **Transferred in**—Count of contacts transferred to a queue\.
+ **Transferred out**—Count of contacts transferred out of a queue\.
+ **Queued**—Number of contacts placed into the queue\.

**To create a routing profiles report with additional metrics for hold time and consult**

1. Choose **Metrics and quality**, **Real\-time metrics**, **Queues**\.

1. To open the **Table settings** menu, select the cog icon\.

1. Choose **Metrics**\.

1. For **Hold time** and **Consult**, select the metrics options\.

1. Choose **Save**\.

To display other types of reports, choose **New Table** and select the type of report to see\. To remove a report, choose **x** on the top\-right corner of the report\.