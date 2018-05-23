# Amazon Connect Metrics and Reports<a name="connect-metrics"></a>

In Amazon Connect, data about contacts, such as the amount of time a contact spends in each state \(customer on hold, customer in queue, agent interaction time\) are captured in contact trace records \(CTR\)\. The basis for most historical and real\-time metrics in Amazon Connect is the data in the CTR\. When you create metrics reports, the values displayed for most metrics in the report are calculated using the data captured in the CTRs\.

**Note**  
Not all metrics are derived from CTR data\. For example, the **Contacts consulted** metric, which is a count of number of times an agent consulted with a third party, is not included in CTRs\.

Within Amazon Connect, you can generate a number of real\-time and historical metric reports to monitor efficiency and utilization, agent performance, and other information about your contact center\. CTRs are available within your instance for 24 months\. You can also choose to stream CTRs to Amazon Kinesis so that you can manage retention and perform advanced analysis on the data for your contact center\.

To get detailed information on the activity of agents in your contact center, you can use [Agent Event Streams](agent-event-streams.md)\.

## Permissions Required to Access Metrics Reports<a name="report-permissions"></a>

Only users with appropriate permissions can create and view metrics reports\. The **QualityAnalyst** and **CallCenterManager** security profiles include the permissions necessary to access metric data, which allows for viewing metrics reports\. To view metrics reports, a user account must be assigned the **Access** permission for **Access Metrics** under **Metrics and Quality** on the **Security profiles** page\.