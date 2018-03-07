# Agent Event Streams<a name="agent-event-streams"></a>

Amazon Connect agent event streams are Amazon Kinesis data streams that provide you with near real\-time reporting of agent activity within your Amazon Connect instance\. The events published to the stream include agent login, agent logout, agent answers a call, and agent status change\.

You can use the agent event streams to create dashboards that display agent information and events, integrate streams into workforce management \(WFM\) solutions, and configure alerting tools to trigger custom notifications of specific agent activity\. Agent event streams help you manage agent staffing and efficiency\.

## Enabling Agent Event Streams<a name="agent-event-streams-enable"></a>

Agent event streams are not enabled by default\. Before you can enable agent event streams in Amazon Connect, create a data stream in Amazon Kinesis Data Streams\. Then, choose the Kinesis stream as the stream to use for agent event streams\. Though you can use the same stream for both agent event streams and contact trace records, managing and getting data from the stream is much easier when you use a separate stream for each\. For more information, see the [Amazon Kinesis Data Streams Developer Guide](http://docs.aws.amazon.com/streams/latest/dev/)\.

**Note**  
If you enable server\-side encryption for the Kinesis stream you select for agent event streams, Amazon Connect cannot publish to the stream because it does not have permission to kms:GenerateDataKey\. No records are published to the stream\.

**To enable agent event streams**

1. Open the Amazon Connect console at [https://console\.aws\.amazon\.com/connect/](https://console.aws.amazon.com/connect/)\.

1. On the console, choose the name in the **Instance Alias** column of the instance for which to enable agent event streams\.

1. Choose **Data streaming**, then select **Enable data streaming**\.

1. Under **Agent Events**, select the Kinesis stream to use, and then choose **Save**\.

## Agent Event Streams Data Model<a name="agent-event-stream-model"></a>

Agent event streams are created in JavaScript Object Notation \(JSON\) format\. For each event, a JSON blob is sent to the Kinesis data stream\. Each blob includes data about the event, as described in the following table\.


| Agent event type | Description | 
| --- | --- | 
|  LOGIN  |  Agent login to the contact center\.  | 
|  LOGOUT  |  Agent logout from the contact center\.  | 
|  STATE\_CHANGE  |  One of the following changed: Agent configuration, such as profile or the assigned hierarchy group\. Agent state in the contact control panel, such as Available\. Agent conversation state, such as on hold\.  | 
|  HEART\_BEAT  |  This event is published every 120 seconds if there are no other events published during that time\.  | 

The following table described the fields in the `AgentEvent` object\.


| Field | Type | Description | 
| --- | --- | --- | 
|  Version  |  String  |  The version of the agent event stream in date format, such as 2017\-10\-10\.  | 
|  EventId  |  String  |  Universally unique identifier \(UUID\) for the event\.  | 
|  AWSAccountId  |  String  |  The 12\-digit AWS account ID for the AWS account associated with the Amazon Connect instance\.  | 
|  InstanceARN  |  String  |  Amazon Resource Name for the Amazon Connect instance where the agent’s user account is created\.  | 
|  AgentARN  |  String  |  The Amazon Resource Name for the agent\.  | 
|  EventTimestamp  |  String  |  A time stamp for the event, in ISO 8601 standard format\.  | 
|  EventType  |  String  |  The type of event, one of LOGIN, LOGOUT, STATE\_CHANGE, or HEART\_BEAT\.  | 
|  PreviousAgentSnapshot  |  `AgentSnapshot` object  |  Contains agent configuration, such as username, first name, last name, routing profile, hierarchy groups\), contacts, and agent status\. Not applicable to Login or Logout events\.  | 
|  CurrentAgentSnapshot  |  `AgentSnapshot` object  |  Contains agent configuration, such as username, first name, last name, routing profile, hierarchy groups, contacts, and agent status\.  | 

The following table describes the properties of the `AgentSnapshot` object\.


| Field | Type | Description | 
| --- | --- | --- | 
|  Configuration  |  `Configuration` object\.  |  Information about the agent, including: Username FirstName LastName RoutingProfile HierarchyGroups  | 
|  AgentStatus  |  `AgentStatus` object  |  Agent status data, including: AgentARN \- the ARN for the agent status\. Name \- the name of the status, such as Available or Offline\.  | 
|  Contacts  |  List of `Contact` objects  |  List of contacts  | 

The following table describes the `Configuration` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  UserName  |  String  |  The user name for the agent’s Amazon Connect user account\.  | 
|  FirstName  |  String  |  The first name entered in the agent's Amazon Connect account\.  | 
|  LastName  |  String  |  The last name entered in the agent's Amazon Connect account\.  | 
|  RoutingProfile  |  `RoutingProfile` object\.  |  The routing profile for the agent associated with the event\.  | 
|  HierarchyGroups  |  `HierarchyGroups` object\.  |  The hierarchy group, up to five levels of group, for the agent associated with the event\.  | 

The following table describes the `AgentStatus` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  ARN  |  String  |  The Amazon Resource Name for the agent status\.  | 
|  Name  |  String  |  The name of the status event\. Values include the following plus any custom values you have defined: Available Offline  | 
|  StartTimestamp  |  Timestamp  |  The time at which the agent event occurred, in ISO 8601 format\. This is the time at which the agent changed from one status to another\.  | 

The following table describes the `RoutingProfile` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  ARN  |  String  |  Amazon Resource Name for the agent's routing profile\.  | 
|  Name  |  String  |  The name of the routing profile\.  | 
|  InboundQueues  |  List of `Queue` objects\.  |  A list of `Queue` objects associated with the agent's routing profile\.  | 
|  DefaultOutboundQueue  |  `Queue` object  |  The default outbound queue for the agent's routing profile\.  | 

The following table describes the `Queue` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  ARN  |  String  |  Amazon Resource Name for the queue\.  | 
|  Name  |  String  |  The name of the queue\.  | 

The following table describes the `HierarchyGroups` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  Level1  |  `HierarchyGroup` object\.  |  Includes details for Level1 of the hierarchy assigned to the agent\.  | 
|  Level2  |  `HierarchyGroup` object  |  Includes details for Level2 of the hierarchy assigned to the agent\.  | 
|  Level3  |  `HierarchyGroup` object  |  Includes details for Level3 of the hierarchy assigned to the agent\.  | 
|  Level4  |  `HierarchyGroup` object  |  Includes details for Level4 of the hierarchy assigned to the agent\.  | 
|  Level5  |  `HierarchyGroup` object  |  Includes details for Level5 of the hierarchy assigned to the agent\.  | 

The following table describes the `HierarchyGroup` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  ARN  |  String  |  The Amazon Resource Name for the agent hierarchy\.  | 
|  Name  |  String  |  The name of the hierarchy group\.  | 

The following table describes the `Contact` object properties\.


| Field | Type | Description | 
| --- | --- | --- | 
|  ContactId  |  String  |  UUID identifier for the contact  | 
|  InitialContactId  |  String  |  The ContactId of the original contact that was transferred\.  | 
|  Channel  |  String  |  Enumeration of the method of communication, such as Voice\.  | 
|  InitiationMethod  |  String  |  Enumeration of how the contact was initiated: Inbound Outbound Transfer Callback  | 
|  State  |  String  |  An enumeration of the state of the contact: INCOMING PENDING CONNECTING CONNECTED CONNECTED\_ONHOLD MISSED ERROR ENDED  | 
|  StateStartTimestamp  |  String  |  A time stamp for the time at which the contact entered the State\.  | 
|  ConnectedToAgentTimestamp  |  String  |  A time stamp for the time the contact was connected to an agent\.  | 
|  QueueTimestamp  |  String  |  A time stamp for the time at which the contact was put into a queue\.  | 
|  Queue  |  Queue object  |  The queue the contact was placed in\.  | 