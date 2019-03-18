# Historical Metrics Reports<a name="historical-metrics"></a>

Historical metrics reports include data about past, completed activity and performance in your contact center\. You can generate the following reports for historical metrics in Amazon Connect\. Metrics for agent queues are not included in reports by default\.
+ Queues
  + Contact metrics
  + Agent metrics
+ Agents
  + Agent performance
  + Agent activity audit
+ Phone numbers
  + Contact metrics

The report selections use the same metrics, but group and order the data in the report a different way\. Which fields that are included in a historical metrics report depends on the type of report and the grouping for the report\.

You can customize the default report settings to get the view of the data that is most meaningful to you and your organization\. You can change the time frame for the report, which metrics are included in the report, and how the data is grouped within the report\.

# About Custom Agent Statuses

You can create custom statuses for agents\. These custom statuses are included only in some reports with some grouping options\. For example, they are not included in **Queue Agent Metrics** reports that are grouped by queue\.

## Create a Historical Metrics Report<a name="create-historical-metrics-report"></a>

You can create historical metrics reports to view historical data for activity in your contact center\.

1. Log in to your Amazon Connect instance\.

1. Choose **Metrics and Quality**, **Historical metrics**\.

1. Select the type of report to create\.

   If you choose a **Queues**, **Agent performance**, or **Phone numbers**, the report is generated when you choose the report type\.

1. To create an **Agent activity audit** report, choose **Agent activity audit**, then select an agent in the **Agent Login** list and specify the **Date** and **Time Zone** to use for the report\.

   You can filter reports by **Agent** or **Routing Profile** in the **Filter by** drop\-down menu\.

## Add a Report to the Dashboard<a name="add-hist-metrics-report"></a>

You can add multiple real\-time metrics reports to the dashboard to get different views of the activity in your contact center\.

1. Create a Historical metrics report\.

1.  On the **Historical metrics** page, choose **New table**, and then the report type to add, **Queue**, **Routing profiles**, or **Agents**\.

    A new report table is added to the page using the default report template\.

1. Optionally, customize the report to get the view you want\. Making changes to the added table does not affect the other tables already on the page\.

## Include Agent Queues in Historical Metric Reports<a name="add-agent-queue-metrics"></a>

By default, agent queues are excluded from historical metrics reports\. To include agent queues in the report, select agent queues as a filter for the report\.

**Include agent queues in historical metric reports**

1. Create a historical metrics report\.

1. Choose the cog icon near the top\-right corner of the report to open the report settings\.

1. Choose the **Filters** tab\.

1. Select the **Show agent queues** check box\.

1. Select **Agent queues**\.

1. Under **Agent queues**, select the agent queues to include in the report in the drop\-down list\.

1. Choose **Apply**\. The report now shows metric data for the selected agent queues\.

## Save a Historical Metrics Report<a name="save-hist-metrics-reports"></a>

When you create the report you want, you can save it so that you can access it in the future\. Instead of customizing the default report template, you can just open the saved report to view it\.

1. After you customize a report, choose **Save** or **Save As**\.

   If you previously saved the report, when you choose **Save** the updated report is saved over the previous version\.

1. If you choose **Save as**, or **Save** for a report that you have not saved previously, provide a name for your report\.

1. Choose **Save** or **Save as**\. 

You can access the saved report from the **Saved reports** page by choosing **Metrics and Quality**, **Saved reports**, and then choose the **Historical metrics** tab\.

## Download a Historical Metrics Report as a \.csv File<a name="hist-metrics-download"></a>

You can download the data included in your report as a comma\-separated value \(\.csv\) file so that you can use it with other applications\. When you download the report, the fields included in the report are the same as the metrics you selected for the report\. Metrics for which there is no data to include in the report show a dash in the downloaded \.csv file\.

1. Create and customize the report to download\.

1. Choose the down arrow next to **Save** in the top\-right corner of the page\.

1. Choose **Download CSV**\.

1. Confirm the action to take for the file in the browser dialog displayed\.

## Clear the Historical Metrics Dashboard<a name="clear-historical-dashboard"></a>

If you want to create a new dashboard, you can remove all of the report tables you added to your dashboard at once\.

1. Choose the down arrow next to **Save** in the top\-right corner of the page\.

1. Choose **Clear**\. 

## Customize Historical Metrics Reports<a name="customize-historical-metrics"></a>

When you change the settings for a report you have open, the report displayed on the page is updated to reflect the new settings, but those settings changes to not affect the default report displayed\. You can save the changes to a new report, and then open that report from the Saved reports page\. You can also set a schedule for the report to generate a report with your settings with the recurrence you define\.

Note that scheduling a report also makes the report accessible by any other users in your Amazon Connect instance that have permissions to view Saved reports\. Any user with sufficient permissions can also modify your scheduled report\. Scheduled reports are saved as \.csv files in the Amazon Simple Storage Service \(Amazon S3\) bucket defined for reports in your instance\. You can choose to add a prefix to the report files sent to Amazon S3 on the **Delivery Options** tab of the **Schedule Report** settings\.

**Important**  
For scheduled reports, there is a delay of 15 minutes after the scheduled report time before the report is generated\. This is to ensure that the report includes all of the data about activity that occurred during the time range specified for the report\. Data from your contact center is not immediately processed and available to include in reports, so some data from the time range may not be captured in a report if the report is generated at the second the time range ends\. For example, if you create a scheduled report for time frame of 8:00 AM to 5:00 PM, and there is activity in your contact center between 4:46:00 PM and 4:59:59 PM, the data about that activity may not be aggregated prior 5:00 PM when the report is scheduled to generate\. Instead, the report is generated after 5:15 PM, by which time the data for the last 15 minutes of the time range is included in the report\.

### Table Settings<a name="customize-historical-table-settings"></a>

To change the setting for a historical metrics report, choose the cog icon near the top\-right corner of the report page\.

You can change the following settings when you create a historical metrics report:

#### Interval & Time Range<a name="historical-time-range"></a>

Specify values for the following settings for your report:
+ **Interval**—Choose the interval for displaying data in the report **30 Minutes**, **Daily**, or **Total**\. If you select **30 Minutes**, the report is displayed with a row of data for each 30 minute period during the time range for the report\. When you select **Daily**, the report includes a row for each day in the time range per grouping option, such as queue\. When you select **Total**, all of the data for the entire time range is displayed as a single row on the report\.
+ **Time range**—select the time range for data to include in the report\. When the report is exported to your Amazon S3 bucket, the file name for the exported file includes the date and the UTC time at which the report was created\. The **Last modified date** for the file is displayed using the time zone for the Amazon S3 bucket, and may not match the creation time for the report in UTC time\. When you choose a time range, the hour at which a day starts is determined by the time zone selected\. Reports default to UTC for the time zone\. To generate reports that match your calendar days, select the time zone for your area, or the region in which you created your instance\.

  The selections available for the **Time range** depend on the **Interval** you select\. You can choose from the following values:
  + **Today \(since 12 am\)**—include metrics for the current calendar day starting at 12 AM in the selected time zone\.
  + **Last 24 hours**—Displays data for the previous 24 hours from the current time\.
  + **Yesterday**—include metrics for the previous calendar day, determined by the time zone selected\.
  + **Last 2 days**—include metrics for the previous 2 calendar days, determined by the selected time zone\. The report does not include data from the current day\.
  + **Last 3 days**—include metrics for the previous 3 calendar days, determined by the selected time zone\. The report does not include data from the current day\.
  + **Last 7 days**—include metrics for the previous 7 calendar days, determined by the selected time zone\. The report does not include data from the current day\.
  + **Last week \(Sun – Sat\)**—include metrics for the previous calendar week, from Sunday at 12:00:00 AM to Saturday at 11:59:59 PM\. The final second of the day is included in the data included in the report\.
  + **Month to date**—include metrics for the days in the current calendar month up to 12:00:00 AM the current day\. Metrics from the current day, which starts at midnight in the selected time zone, are not included\.
  + **Last 30 days**—include metrics from the previous 30 calendar days, determined by the time zone selected\. Data for the current day is not included in the report\.
  + **Previous month**—include metrics for the previous calendar month, determined by the time zone selected\.
  + **Custom time range**—choose a custom time range for the report\.
+ **Time Zone**—Select the time zone to use for the report\. The time zone you choose is important, as the start and end of a calendar day is determined by the time zone you choose\. If your local time is in a different time zone than the time zone selected for reports, the report uses 12:00:00 AM in the time zone selected, and not the time zone you are in\. For example, if your organization uses times in the US\-Pacific time zone, UTC\-8, the calendar day starts 8 hours after midnight UTC time, or 4 PM local time\. If you use UTC for the time zone for reports, the calendar day for the report is from 4 PM to 4 PM in your time zone rather than 12:00 AM to 12:00 AM\. If your agents are staffed for shifts that end at 5 PM, your daily report includes agent metrics data for their shift until 4 PM local time\. The remaining hour between 4 PM to 5 PM is included in the next calendar day when UTC time is selected for the report\.

  You should use the same time zone for reports over time to get accurate and consistent metrics data for your contact center\. Using different time zones for different reports may result in different data for the same time range selection\.

#### Groupings<a name="hist-metrics-groupings"></a>

You can select from the following settings for grouping, or organizing, data in the report\.
+ **Grouping options**—choose the \+ next to an option to move it to the **Selected groupings** column\. Report data is displayed in the report grouped by the fields in the **Selected groupings** column\. For example, if you select Total for a time interval, and select **Queue** as the grouping option, the queue name is displayed as the first column in the report\. If you select a time interval other than Total, the time interval is displayed as the first column in the report\.

  Report data, such as average times and contacts handled, reflect the values for the queue under which they are grouped\. If you choose **Agent** as the grouping option, the first column in the report is the agent name, and the data in the report reflects averages and contacts handled for each agent across all queues and routing profiles\. The metrics you include on a report can be grouped in different ways to provide greater insight into how your contact center is performing\.

  You can group reports on the following:
  + **Agent**
  + **Agent Hierarchy Level One**
  + **Agent Hierarchy Level Two**
  + **Agent Hierarchy Level Three**
  + **Agent Hierarchy Level Four**
  + **Agent Hierarchy Level Five**
  + **Phone Number**
  + **Queue**
  + **Routing Profile**

  You can select only one agent hierarchy at a time for grouping\. If you have not defined any agent hierarchies, the grouping option is greyed out and not selectable\.
+ **Selected groupings \(Maximum 5\)**—you can choose to group report data by up to 5 of the available grouping options\. When only one grouping option is selected, all report data is grouped by that option\. When more than one option is selected, report data is first grouped by the grouping option that is first in the list, and then those records are grouped within that group by the additional grouping option added to the **Selected groupings** column\. 

#### Understanding How Grouping Affects Historical Metrics Calculations

When you create a report, the values for calculated metrics are displayed as rows in the report\. The rows in the report are grouped by the grouping option you select\. The grouping of the data allows you to generate global data for your contact center, or more specific data for queues, agents, routing profiles, or agent hierarchy defined in your contact center\. The metric calculations, and therefore metrics values displayed in the report, are different when reports are grouped differently\. If you group the report results by queue, the value displayed for a metric is inclusive of all contacts associated with the queue\. 

For example, consider the **Contacts handled** metric\. This metric is a count of the contacts handled during the time range defined for the report\. With the default grouping, **Queue**, the value for **Contacts handled** is the total number of contacts handled during the time range from that queue by all agents in your contact center\.
+ If you group the report by **Agent**, the **Contacts handled** metric is the total number of contacts handled by the agent during the time range across all queues and routing profiles\.
+ If you group the report by routing profile, only contacts handled by agents assigned the routing profile and included in the count of contacts handled\.
+ If you group the report by queue, then agent, then routing profile, the value for **Contacts handled** is the total number of contacts an agent that is assigned the routing profile handled from the queue\.

Agent activity can be included in one routing profile at a time, but agents can switch between routing profiles over the reporting time interval\. If agents are assigned multiple routing profiles and handle contacts from multiple queues, there are multiple rows in the report for each routing profile assigned to the agent and the queue that the agent handled contacts from\.

#### How Metrics Data Differs by Report Type

When you generate a report, the values displayed for each metric may be different for each report type or grouping option you choose\. Some grouping options are more meaningful for some report types than for others\. If you group a report by agent, the values for metrics associated with queues may not provide much insight\. For some reports, you cannot add some metrics, select some grouping options, or use some filters\. For example:
+ When you group a report by queue, the metric values displayed reflect data for the metric grouped for the queue during the specified time range\. If you look at the value for the Average Customer Hold time, it shows the average amount of time that customers spent on hold for each queue\.
+ When you group the report by agent, the metric values displayed reflect data for the metric grouped by agent\. The value for Average customer hold time shows the average time for each agent across all queues to which the agent is assigned\.
+ When the report is grouped by Routing profile, the report shows the value for metrics grouped by routing profile, so will show Average Customer hold time by routing profile\. 

You can customize the metrics reports to get the view of your contact center that makes the most sense for your organization\.

#### Filters<a name="hist-metrics-filters"></a>

You can select filters for your report to limit the data included in a report to a specific category, such as queue or routing profile\. When you select filters, the numbers of filters you selected is displayed next to the filter category\. The fields available to select for filtering depends on the grouping selected for a report\.

You must select at least one metric for a report\. An exclamation point \(\!\) is displayed next to any metrics that are not available to include in the report with the selected grouping\. 

You can filter on the following categories:
+ **Queue**—Select one or more queues for which you want to include data in the report\. If you do not select any queues, all queues are included in the report\. You can search for a queue by typing the name of the queue in the Search field, or scroll through the queues listed in the drop\-down list, and then select the check box to filter the report results to that queue\.
+ **Routing profile**—Select one or more routing profiles for which you want to filter data in the report\. When you choose a routing profile, data is displayed only for the agents that are assigned that routing profile\. If you do not select any routing profiles, agent data for all routing profiles is included in the report\. To select a routing profile, type the name of the profile in the Search box, or scroll through the drop\-down list\. Select the check box next to one or more profiles to filter results in the report\.
+ **Agent hierarchy**—Select one or more agent hierarchies to filter data in the report to contacts handled by agents in the selected hierarchy\. If you do not select a hierarchy, data for all contacts handled by agents in all hierarchies is included in the report\. When only one hierarchy is selected, you can select a more granular filter within the hierarchy\.
+ **Phone number**—Select one or more phone numbers for your contact center to filter report data to include only contacts associated with the phone number or numbers selected\. If you do not select a phone number, data for contacts on all phone numbers is included in the report\.

**Clear a Selected Filter**  
If you want to remove one of the filters you selected for a report, you can either deselect the check box next to the filter in the drop\-down list, or choose the x next to the filter name displayed below the **Search** field on the **Filters** tab\.

#### Metrics<a name="hist-metrics-metrics"></a>

Choose the metrics or fields to include in the report\. Only the metrics you select are displayed in the report and included in report data stored in Amazon S3\. The selections you make do not affect which metrics are calculated, generated, and included in contact trace records\. To see different data for a time range, you can create another report and use different filters or groupings without affecting other reports or the default reports in Amazon Connect\. The definitions for each metric are included in the following section\.

## Historical Metrics Definitions<a name="hist-metrics-definitions"></a>

The following metrics are available to include in historical metrics reports in Amazon Connect\.

**Agent Name**  
 The agent’s name, displayed as Last name, First name\.

**Agent First Name**  
The agent’s first name as entered in their Amazon Connect user account\.

**Agent Last Name**  
The agent’s last name as entered in their Amazon Connect user account\.

**After contact work time**  
Sum of the amount of time spent in After Contact Work \(ACW\) status after handling contacts\. Agents enter ACW status after they end a call with a customer\. ACW status ends when the agent changes to a different status\.  
You can specify an After call work timeout value in user profiles\.

**Agent on contact time**  
Sum of time that an agent was on a contact, including hold time and after call work\. Most of the time, this is calculated with the following formula:  
`Agent on Contact time = AgentInteractionDuration + CustomerHoldDuration + After contact work time` \(including callbacks\)\.  
In some cases, the value reported for this metric also includes agent time spent in an auxiliary state\. The time in the auxiliary state is included in the metric value, but not available in the CTR or as a separate metric\.

**Agent idle time**  
Sum of time that an agent spent in a productive status, but not handling contacts\. A productive status is any status other than **Offline** or any custom agent status that you create\.

**Non\-Productive Time**  
Amount of time agents spent in a status other than Error or Offline, but was not handling contacts\.

**Average queue abandon time**  
Average amount of time that customers spent in a queue before abandoning the call\. This is calculated by averaging the difference between the `EnqueueTimestamp` and `DequeueTimestamp` for contacts that were abandoned while in a queue\. Any call that was placed in a queue but not picked up by an agent or transferred to a callback is considered an abandoned call\.

**Average after contact work time**  
Average time that an agent spent in After contact work time status\. This is calculated by averaging the `AfterContactWorkDuration` for all contacts included in the report based on the selected filters\.

**Average queue answer time**  
Average of time that contacts were in a queue before being answered by an agent\. This is the average for `QueueInfo`:`Duration`\.

**Average handle time**  
Average of **Contact handle time** for all contacts handled by the agent\. **Contact handle time** is the time an agent spent on a contact, including after call work\.

**Average customer hold time**  
The average of `CustomerHoldDuration` \(from the CTR\), which is time customers spent on hold after being connected to an agent\.

**Average agent interaction and customer hold time**  
Average of the sum of agent interaction and customer hold time\. This is calculated by averaging the sum of `AgentInteractionDuration` plus `CustomerHoldDuration`\.

**Average agent interaction time**  
Average amount of time that agents interacted with customers on contacts\.

**Contacts abandoned**  
Number of contacts when the customer disconnected while waiting in a queue before being connected to an agent\. Calls that transfer to callbacks are not counted as abandoned\.

**Contacts abandoned in 15 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 15 seconds\.

**Contacts abandoned in 20 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 20 seconds\.

**Contacts abandoned in 25 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 25 seconds\.

**Contacts abandoned in 30 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 30 seconds\.

**Contacts abandoned in 45 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 45 seconds\.

**Contacts abandoned in 60 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 60 seconds\.

**Contacts abandoned in 90 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 90 seconds\.

**Contacts abandoned in 120 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 120 seconds\.

**Contacts abandoned in 180 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 180 seconds\.

**Contacts abandoned in 240 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 240 seconds\.

**Contacts abandoned in 300 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 300 seconds\.

**Contacts abandoned in 600 seconds**  
Count of contacts when the customer disconnected while in the queue for less than 600 seconds\.

**Contacts agent hung up first**  
Count of contacts when the agent disconnected before the customer\.

**Contacts consulted**  
Count of contacts when an agent consulted with a third party\. The agent interacts with the third party, but the customer is not transferred to the third party\.

**Contacts handled**  
Count of contacts handled by an agent, including both incoming and outgoing contacts\.

**Contacts handled incoming**  
Count of incoming contacts that were handled by an agent, including the following types of contacts:  
+ Inbound calls
+ Transfer to agent
+ Transfer to queue
+ Queue to queue transfer

**Contacts handled outbound**  
Count of outbound contacts that were handled by an agent\. This includes contacts that were initiated by an agent using the CCP\.

**Callback contacts handled**  
The total number of contacts handled by an agent that were initiated from a queued callback\.

**API Contacts handled**  
Total number of contacts handled by an agent that were initiated using an Amazon Connect API operation, such as `StartOutboundVoiceContact`\.

**Contacts put on hold**  
Count of contacts put on hold by an agent one or more times\.

**Contacts hold disconnect**  
Count of contacts disconnected while the customer was on hold\. This includes both the agent and the customer ending the contact\. 

**Contacts hold agent disconnect**  
Count of contacts that were disconnected by the agent while the customer was on hold\.

**Contacts hold customer disconnect**  
Count of contacts that were disconnected by the customer while the customer was on hold\.

**Contacts incoming**  
Count of incoming contacts to your Amazon Connect instance\. This is the count of contacts that were initiated outside of Amazon Connect, or contacts transferred within Amazon Connect, including the following types of contacts:  
+ Inbound calls
+ Transfer to agent
+ Transfer to queue
+ Queue to queue transfer

**Callback contacts**  
The total number of contacts initiated from a queued callback\.

**API Contacts**  
Total number of contacts initiated using an Amazon Connect API operation, such as `StartOutboundVoiceContact`\.

**Contacts answered in 15 seconds**  
Count of contacts that were answered by an agent within 15 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 20 seconds**  
Count of contacts that were answered by an agent within 20 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 25 seconds**  
Count of contacts that were answered by an agent within 25 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 30 seconds**  
Count of contacts that were answered by an agent within 30 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 45 seconds**  
Count of contacts that were answered by an agent within 45 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 60 seconds**  
Count of contacts that were answered by an agent within 60 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 90 seconds**  
Count of contacts that were answered by an agent within 90 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 120 seconds**  
Count of contacts that were answered by an agent within 120 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 180 seconds**  
Count of contacts that were answered by an agent within 180 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 240 seconds**  
Count of contacts that were answered by an agent within 240 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 300 seconds**  
Count of contacts that were answered by an agent within 300 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts answered in 600 seconds**  
Count of contacts that were answered by an agent within 600 seconds of being placed in a queue, based on the `EnqueueTimestamp`\.

**Contacts queued**  
Count of contacts placed into a queue\.

**Contacts transferred in**  
Count of contacts transferred to a queue by an agent using the CCP\.

**Contacts transferred out**  
Count of contacts transferred out of a queue after being answered by an agent\.

**Contacts transferred out internal**  
Count of contacts for the queue that were transferred by an agent to an internal source, such as a queue or another agent\. An internal source is any source that can be added as a Quick Connect\.

**Contacts transferred out external**  
Count of contact for the queue that were transferred to an external source, such as a phone number that is external to your contact center\.

**Contacts transferred in from queue**  
The number of contacts transferred in to the queue from another queue in a Transfer to queue contact flow\.

**Contacts transferred out from queue**  
The number of contacts transferred from this queue to another queue in a Transfer to queue contact flow\.

**Error status time**  
Sum of time that an agent spent in the **Error** status\.

**Customer hold time**  
Sum of the time that customers spent on hold after being connected to an agent\. This includes time spent on a hold when being transferred, but does not include time spent in a queue\.

**Agent answer rate**  
Percentage of contacts routed to an agent that were successfully answered\. Calculated by the following:  
`(Contacts Handled / Contacts Routed) * 100`

**Maximum queued time**  
The longest amount of time that a customer spent waiting in a queue during the time interval for the report\.

**Contacts missed**  
Count of the contacts missed\. A contact is considered missed when it is routed to an agent but the agent did not accept the call for any reason\. The same contact may be counted as missed multiple times, once for each time it is routed to an agent but then not picked up by an agent\.

**Contact handle time**  
Sum of time that an agent spent on contacts, including hold time and **After contact work time**\.

**Contact flow time**  
The time a contact spent in a contact flow\.  
Outbound contacts do not start in a contact flow, so outbound contacts are not included in the metric\.

**Occupancy**  
The percentage of time that agents were active on contacts\. This is calculated by:  
`Agent Handle Time/(Agent Handle Time + Agent Idle Time)`

**Service level 15 seconds**  
Percentage of contacts answered within 15 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 20 seconds**  
Percentage of contacts answered within 20 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 25 seconds**  
Percentage of contacts answered within 25 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 30 seconds**  
Percentage of contacts answered within 30 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 45 seconds**  
Percentage of contacts answered within 45 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 60 seconds**  
Percentage of contacts answered within 60 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 90 seconds**  
Percentage of contacts answered within 90 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 120 seconds**  
Percentage of contacts answered within 120 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 180 seconds**  
Percentage of contacts answered within 180 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 240 seconds**  
Percentage of contacts answered within 240 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 300 seconds**  
Percentage of contacts answered within 300 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Service level 600 seconds**  
Percentage of contacts answered within 600 seconds after being placed in a queue, based on the **EnqueueTimeStamp**\.

**Online time**  
Sum of the time that an agent spent in a status other than Offline\. The time that an agent spends in any custom status you define for your instance is considered online, non\-productive time\. 

**Agent interaction and hold time**  
Sum of **Agent interaction time** \+ **Customer hold time**\.

**Agent interaction time**  
Sum of the time that agents spent interacting with customers\. For calls, this is the amount of time agents spent talking to customers on the call\.

**Average outbound agent interaction time**  
Average time agents spent interacting with a customer during an outbound contact\.

**Average outbound after contact work time**  
Average time that agents spent in ACW status after outbound contacts\.