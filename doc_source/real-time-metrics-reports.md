# Real\-time Metrics Reports<a name="real-time-metrics-reports"></a>

Real\-time metrics reports show real\-time or near\-real time metrics information about activity in your contact center\. Metrics such as **Online** show the number of agents currently online in real\-time, updating every 15 seconds\. Metrics such as **Handled** and **Abandoned** reflect near real\-time values for your contact center\. Data in Real\-time reports is refreshed as follows:
+ The report page updates every 15 seconds\.
+ Metrics such as **Active** and **Availability** update as activity occurs, with a small system delay for processing the activity\.
+ Agent near real\-time metrics, such as **Missed** and **Occupancy**, update every 5 minutes\.
+ Contact near real\-time metrics update about 1 minute after a contact ends\.

Report templates are included for **Queues**, **Agents**, and **Routing profiles**\. You can also customize each of the report types, specify a time range for the report, and select filters for fields to include or exclude from the report\. You can add additional reports, or display multiple versions of the same report type, and customize each to include different information or a different time range\. Updating one report does not affect the other reports displayed on the report page\. When you create a real\-time metrics report, it is displayed on the Real\-time metrics page, and updates automatically to show current activity in your contact center\.

## Types of Real\-time Metrics Reports<a name="types-real-time-reports"></a>

You can create the following types of real\-time metrics reports in Amazon Connect\.

**Queues**  
Queues reports show contact data grouped by queue\. For each contact that occurred during the report time range, the queue in which the contact was handled is displayed with metrics about Agent and Performance\. When you create a Queues report, the first column in the report table is Queues, and the data in the table is data for the queue\. You can view the routing profile associated with the queue by selecting the arrow next to the queue name\.  

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-rtm-queue-show-profile.png)
If you choose the view agents icon next to the routing profile, a report table for the routing profile is added to the page\.

**Agents**  
Agents reports show data about agents currently online in to your contact center, grouped by agent\. Only agents with a status of **Online** are included\. When you create an Agents report, the first column in the report is the **Agent Login**, which is the agent’s user name used to log in to Amazon Connect\. The data in the report includes metrics for **Agent**, **Phone**, and **Performance**\.

**Routing profiles**  
Routing Profiles reports display data about activity in your contact center grouped by routing profile, and includes metrics for Agents and Performance\.

## To create a real\-time metrics report

1. Log in to your contact center using an account that has at least Access permission for Access metrics\. The **QualityAnalyst** and **CallCenterManager** security profiles include this permission\.

1. Choose **Metrics and Quality**, **Real\-time metrics**\.

1. Choose the report type to create, **Queues**, **Agents**, or **Routing profiles**\.

1. Optionally, select the number of rows to include per page, **5**, **10**, **20**, or **50**\.

1. Customize the report to provide the view of your contact center that you want\. For more information, see [Customize Real\-time Metrics Reports](#customize-real-time-reports)\.

For **Queues** and **Routing profiles** reports, the first row of the report is a summary of the activity included in the report\. You can hide the report and display only the summary row by choosing the up or down arrow displayed near the top\-right corner of the report table\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect-rtm-report-hide-report.png)

## View real\-time metrics for agent queues<a name="real-time-agent-queues"></a>

To view a real\-time metric report for agent queues, you can add an **Agent queues** table to the dashboard\. This adds a report to the dashboard that includes metric data for the agent queues in your instance\. To add an agent queue report, choose the down arrow next to **New table**, then choose **Agent queues**\.

## Customize Real\-time Metrics Reports<a name="customize-real-time-reports"></a>

You can customize real\-time metrics report you create to get the view of your contact center that is the most meaningful for your organization\. To customize your report, choose the cog icon near the top\-right corner of the report table\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/connect/latest/userguide/images/connect_report_settings_icon.png)

The following settings are common to all real\-time metrics reports\.

On the **Time Range** tab:
+ Trailing windows for time \- the previous X hour\(s\)—select the time range, in hours, for data included in the report displayed on the Real\-time metrics dashboard\. You can select from the following values:
  + \.5
  + 1
  + 2
  + 4
  + 8
  + 12
  + 24
+ **Midnight to now**—display data for your contact center from midnight to the current time in the Time Zone selected\. If you select a time zone other than the one you are currently in, the data reflects activity starting at midnight for the calendar day in that time zone, not your current time zone\.

On the **Filters** tab:
+ **Primary filter**—select whether to include all data from your contact center in the report tables, or include only the data for the specific items you select in the **Include** drop\-down\. You can select from the following filters:
  + **All**—data for all activity in your contact center is included in the report\.
  + **Queues**—when you select **Queues**, the queues in your contact center are displayed in the Include drop\-down\. You can select one or more queues to include in the report\. Data for queues not selected is not included in the report\.
  + **Routing profiles**—when you select **Routing profiles**, you can filter data included in the report to include only data from the routing profiles you select in the Include drop\-down\.
  + **Agent Hierarchies**—select which agent hierarchies to display data for in the report\. This filter is available only for **Agents** reports\. 

On the **Metrics** tab:

Select the metrics to include in the report\. The metrics available depend on the type of report\.
+ For **Queues** reports, metrics for **Agents** and **Performance** are included\.
+ For **Agents** reports, metrics for **Agent**, **Phone**, and **Performance** are included\.
+ For **Routing profiles** report, metrics for **Agents** and **Performance** are included\.

 For details about each metric, see [Real\-time Metrics Available in Amazon Connect](#real-time-metrics-definitions)\. 

## Save a Real\-time Metrics Report<a name="save-real-time-metrics-reports"></a>

When you create the report you want, you can save it so that you can access it in the future\. Instead of customizing the default report template, you can just open the saved report to view it\.

1. After you customize a report, choose **Save** or **Save As**\.

   If you previously saved the report, when you choose **Save** the updated report is saved over the previous version\.

1. If you choose **Save as**, or **Save** for a report that you have not saved previously, provide a name for your report\.

1. Choose **Save** or **Save as**\. 

You can access the saved report from the **Saved reports** page by choosing **Metrics and Quality**, **Saved reports**, and then choose the **Real\-time metrics** tab\.

## Download a Real\-time Metrics Report as a \.csv File<a name="download-real-time-report"></a>

You can download the data included in your report as a comma\-separated value \(\.csv\) file so that you can use it with other applications\. When you download the report, the fields included in the report are the same as the metrics you selected for the report\. Metrics for which there is no data to include in the report show a dash in the downloaded \.csv file\.

1. Create and customize the report to download\.

1. Choose the down arrow next to **Save** in the top\-right corner of the page\.

1. Choose **Download CSV**\.

1. Confirm the action to take for the file in the browser dialog displayed\.

## Add a Report to the reports page<a name="add-real-time-report"></a>

You can add multiple real\-time metrics reports to the reports page to get different views of the activity in your contact center\.

1. Create a Real\-time metrics report\.

1.  On the **Real\-time metrics** page, choose **New table**, and then the report type to add, **Queue**, **Agent queues**, **Routing profiles**, or **Agents**\.

    A new report table is added to the page using the default report template\.

1. Optionally, customize the report to get the view you want\. Making changes to the added table does not affect the other tables already on the page\.

## Clear the Real\-time metrics Page<a name="clear-real-time-dashboard"></a>

If you want to create a new report page, you can remove all of the report tables you added to your page at once\.

1. Choose the down arrow next to **Save** in the top\-right corner of the page\.

1. Choose **Clear**\.

## Real\-time Metrics Available in Amazon Connect<a name="real-time-metrics-definitions"></a>

The following sections describe the metrics available to include in real\-time metrics reports in Amazon Connect\. The metrics available to include in a report depend on the report type\.

### Metrics Available in Queues and Routing Profiles Reports<a name="metric-descriptions-queue-routing"></a>

The following metrics are available to include in both **Queues** and **Routing profiles** real\-time metrics reports\.

### Agent Metrics<a name="real-time-queue-agent-metrics"></a>

The following agent metrics are included in default reports\.
+ **Online**—Number of agents with a status other than offline\.
+ **On call**—Number of agents currently active on a contact\.
+ **NPT**—Non\-productive time \(NPT\) is the number of agents in a non\-productive status, such as **Unavailable**\.
+ **ACW**—After call work \(ACW\) is the number of agents currently with a status of **After Call Work**\.
+ **Error**—Number of agents in an error status\.
+ **Available**—Number of agents with a status of **Available**\.
+ **Staffed**—Number of agents currently logged in and with a status of **Available**, **On call**, or in **ACW**\.

### Performance Metrics<a name="real-time-queues-performance"></a>

The following performance metrics are included in default reports\.
+ **In queue**—Number of contacts currently waiting in the queue\.
+ **Oldest**—Length of time in the queue for the contact that has been in the queue the longest\.
+ **Scheduled**—Number of customers for which there is a call back scheduled for this queue\.
+ **Queued**—Number of contacts added to the queue during the reporting interval\.
+ **Handled**—Number of contacts in this queue that were answered by an agent\.
+ **Abandoned**—Number of contacts that were abandoned from the queue during the reporting time range\.
+ **AHT**—Average handled time \(AHT\) is the average time, from start to finish, that a contact was connected with an agent\. This is calculated by averaging the amount of time between the call being answered by an agent and the call ending\.
+ **SL 60**—SL refers to service level, and is the number of contacts that were in the queue for less than 60 seconds\.

### Additional Real\-time Metrics Available for Reports<a name="real-time-metrics-additional"></a>

The following metrics are available to include in reports, but are not included in reports by default\.
+ **SL 15**—Number of contact that were in the queue for less than 15 seconds\.
+ **SL 20**—Number of contact that were in the queue for less than 20 seconds\.
+ **SL 25**—Number of contact that were in the queue for less than 25 seconds\.
+ **SL 30**—Number of contact that were in the queue for less than 30 seconds\.
+ **SL 45**—Number of contact that were in the queue for less than 45 seconds\.
+ **SL 90**—Number of contact that were in the queue for less than 90 seconds\.
+ **SL 120**—Number of contact that were in the queue for less than 120 seconds\.
+ **SL 180**—Number of contact that were in the queue for less than 180 seconds\.
+ **SL 240**—Number of contact that were in the queue for less than 240 seconds\.
+ **SL 300**—Number of contact that were in the queue for less than 300 seconds\.
+ **SL 600**—Number of contact that were in the queue for less than 600 seconds\.
+ **Agent hung up**—Number of contact in the queue that ended because the agent hung up before the customer\.
+ **Handled in**—Number of incoming contacts that were handled by an agent and were initiated from one of the following:
  + Inbound call
  + Transfer to agent
  + Transfer to queue
  + Queue to queue transfer
+ **Handled out**—Number of contacts handled by an agent that were initiated by an agent placing an outbound call using the CCP\.
+ **Callback contacts handled**—Number of contacts handled by an agent that were queued callbacks\.
+ **API contacts handled**—Number of contacts handled by an agent that were initiated by an API operation, such as `StartOutboundVoiceContact`\.
+ **Hold abandons**—Number of contact that disconnected while the customer was on hold\. A disconnect could be because the customer hung up while on hold, or that there was a technical issue with the contact while on hold\.
+ **Consult**—Number of contacts in the queue that were handled by an agent, and the agent consulted with another agent or call center manager during the contact\. 
+ **Max Queued**—The longest amount of time that a contact spent in the queue before being connected to an agent or hanging up the call before being connected to an agent\. This includes any contact that was added to the queue, even if the contact was not connected with an agent, such as abandoned contacts\.
+ **Missed**—Number of contacts added to the queue but not answered by agents, including abandoned contacts\.
+ **Avg abandon time**—Average amount of time, in seconds, that abandoned contacts were in the queue before being abandoned\.
+ **Avg queue answer time**—Average amount of time, in seconds, that a contact was in the queue before being answered by an agent\. This is calculated using only the amount of time that the contact was in the queue, and not any time the contact spent in prior steps of the contact flow, such as listening or responding to prompts\.
+ **Avg hold time**—Average amount of time, in seconds, that a contact in the queue was on hold\.
+ **Avg interaction time**—Average amount of time, in seconds, that contacts were connected to and interacting with, agents\. This does not include hold time or time spent waiting in a queue\. 
+ **Avg interaction and hold time**—Average amount of time, in seconds, that contacts in the queue spent interacting with agents and on hold\. This is the same as **Avg hold time** plus **Avg interaction time**\.
+ **Transferred in**—Number of contacts transferred in to the queue during the time range\.
+ **Transferred out**—Number of contacts transferred out from the queue during the time range\.
+ **Transferred in from queue**—Number of contacts transferred into this queue from another queue during a customer queue flow\.
+ **Transferred out from queue**—Number of contacts transferred out of this queue to another queue during a customer queue flow\.

### Metrics Available in Agents Reports<a name="real-time-agent-report-metrics"></a>

The following metrics are available in Agents real\-time metrics reports\.

### Agent Metrics
+ **Agent Name**—the agent’s name, displayed as last name, first name\.
+ **Agent Last Name **—the agent’s last name as entered in their Amazon Connect user account\.
+ **Agent First Name **—the agent’s first name as entered in their Amazon Connect user account\.
+ **Status**—the agent’s current status, such as **Available** or **After Call Work**\.
+ **Duration**—the length of time that the agent has been in the current status\.
+ **Agent Hierarchy**—the hierarchy the agent is assigned to, if any\.
+ **Routing Profile**—the routing profile the agent is assigned to\.

### Phone Metrics
+ **Active**—Displays 1 if the agent is currently active on call, otherwise shows 0\.
+ **Availability**—displays 1 if the agent is currently in Available status, otherwise shows 0\.
+ **Contact State**—shows the state of the most recent contact the agent handled, such as After Call Work\.
+ **Queue**—shows the name of the queue associated with the most recent contact the agent handled\.

### Performance Metrics
+ **Avg ACW**—the average amount of time an agent spent in ACW status during the report time range\.
+ **Missed**—the number of calls missed by the agent during the time range\.
+ **Handled in**—the number of incoming contacts the agent handled during the time range\.
+ **Handled out**—the number of outgoing contacts the agent handled during the time range\.
+ **AHT**—the average amount of time the agent spent handling contacts during the time range\.
+ **Occupancy**—the per cent of time the agent was occupied during the report time range\.