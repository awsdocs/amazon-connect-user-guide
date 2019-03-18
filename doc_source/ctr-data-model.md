# Contact Trace Records Data Model<a name="ctr-data-model"></a>

This document describes the data model for Amazon Connect contact trace records\. Contact trace records capture the events associated with a contact in your Amazon Connect instance\. Real\-time and historical metrics are based on the data captured in contact trace records\. To learn more about contact trace records and metrics in Amazon Connect, see [Amazon Connect Metrics and Reports](connect-metrics.md)\.

## Agent<a name="ctr-Agent"></a>

Information about the agent that handled the contact\.

**AgentInteractionDuration**  
The time, in whole seconds, that the agent talked with the customer\.  
Type: Integer  
Min value: 0

**AfterContactWorkDuration**  
The difference in time, in whole seconds, between `AfterContactWorkStartTimestamp` and `AfterContactWorkEndTimestamp`\.  
Type: Integer  
Min value: 0

**AfterContactWorkEndTimestamp**  
The date and time the agent left the After Contact Work status\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**AfterContactWorkStartTimestamp**  
The date and time the agent entered the After Contact Work status\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**ARN**  
The Amazon Resource Name of the agent\.  
Type: ARN

**ConnectedToAgentTimestamp**  
The date and time the contact was connected to the agent\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**CustomerHoldDuration**  
The time, in whole seconds, that the customer spent on hold while connected to the agent\.  
Type: Integer  
Min value: 0

**HierarchyGroups**  
The agent hierarchy groups for the agent\.  
Type: AgentHierarchyGroups

**LongestHoldDuration**  
The longest time, in whole seconds, that the customer was put on hold by the agent\.  
Type: Integer  
Min value: 0

**NumberOfHolds**  
The number of times the customer was put on hold while connected to the agent\.  
Type: Integer  
Min value: 0

**RoutingProfile**  
The routing profile of the agent\.  
Type: RoutingProfile

**Username**  
The username of the agent\.  
Type: String  
Length: 1\-100

## AgentHierarchyGroup<a name="ctr-AgentHierarchyGroup"></a>

Information about an agent hierarchy group\.

**ARN**  
The Amazon Resource Name \(ARN\) of the group\.  
Type: ARN

**GroupName**  
The name of the hierarchy group\.  
Type: String  
Length: 1\-256

## AgentHierarchyGroups<a name="ctr-AgentHierarchyGroups"></a>

Information about the agent hierarchy\. Hierarchies can be configured with up to five levels\.

**Level1**  
The group at level one of the agent hierarchy\.  
Type: AgentHierarchyGroup

**Level2**  
The group at level two of the agent hierarchy\.  
Type: AgentHierarchyGroup

**Level3**  
The group at level three of the agent hierarchy\.  
Type: AgentHierarchyGroup

**Level4**  
The group at level four of the agent hierarchy\.  
Type: AgentHierarchyGroup

**Level5**  
The group at level five of the agent hierarchy\.  
Type: AgentHierarchyGroup

## ContactTraceRecord<a name="ctr-ContactTraceRecord"></a>

Information about a contact\.

**Agent**  
If this contact successfully connected to an agent, this is information about the agent\.  
Type: Agent

**AgentConnectionAttempts**  
The number of times Amazon Connect attempted to connect this contact with an agent\.  
Type: Integer  
Min value: 0

**Attributes**  
The contact attributes, formatted as a map of keys and values\.  
Type: Attributes  
Members: `AttributeName`, `AttributeValue` 

**AWSAccountId**  
The ID of the AWS account that owns the contact\.  
Type: String

**AWSContactTraceRecordFormatVersion**  
The record format version\.  
Type: String

**Channel**  
The contact channel\.  
Valid values: VOICE

**ConnectedToSystemTimestamp**  
The date and time the customer endpoint connected to Amazon Connect\. For `INBOUND`, this matches `InitiationTimestamp`\. For `OUTBOUND`, `CALLBACK`, and `API`, this is when the customer endpoint answers\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**ContactId**  
The ID of the contact\.  
Type: String  
Length: 1\-256

**CustomerEndpoint**  
The customer endpoint\.  
Type: Endpoint

**DisconnectTimestamp**  
The date and time that the customer endpoint disconnected from Amazon Connect\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**InitialContactId**  
If this contact is related to other contacts, this is the ID of the initial contact\.  
Type: String  
Length: 1\-256

**InitiationMethod**  
Indicates how the contact was initiated\.  
Valid values: `INBOUND` \| `OUTBOUND` \| `TRANSFER` \| `CALLBACK` \| `API` \| `QUEUE_TRANSFER` 

**InitiationTimestamp**  
The date and time this contact was initiated\. For `INBOUND`, this is when the call arrived\. For `OUTBOUND`, this is when the agent began dialing\. For `CALLBACK`, this is when the callback contact was created\. For `TRANSFER` and `QUEUE_TRANSFER`, this is when the transfer was initiated\. For `API`, this is when the request arrived\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**InstanceARN**  
The Amazon Resource Name of the instance\.  
Type: ARN

**LastUpdateTimestamp**  
The date and time this contact was last updated\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**MediaStreams**  
An array of MediaStream objects\.  
Type: MediaStreams

**NextContactId**  
If this contact is not the last contact, this is the ID of the next contact\.  
Type: String  
Length: 1\-256

**PreviousContactId**  
If this contact is not the first contact, this is the ID of the previous contact\.  
Type: String  
Length: 1\-256

**Queue**  
If this contact was queued, this is information about the queue\.  
Type: QueueInfo

**Recording**  
If recording was enabled, this is information about the recording\.  
Type: RecordingInfo

**SystemEndpoint**  
The system endpoint\. For `INBOUND`, this is the phone number that the customer dialed\. For `OUTBOUND`, this is the caller ID phone number that Amazon Connect used to dial the customer\.  
Type: Endpoint

**TransferCompletedTimestamp**  
If this contact was transferred out of Amazon Connect, the date and time the transfer endpoint was connected\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**TransferredToEndpoint**  
If this contact was transferred out of Amazon Connect, the transfer endpoint\.  
Type: Endpoint

## Endpoint<a name="ctr-endpoint"></a>

Information about an endpoint\. In Amazon Connect, an endpoint is the destination for a contact, such as a customer phone number, or a phone number for your instance\.

**Address**  
The value for the type of endpoint\. For TELEPHONE\_NUMBER, the value is a phone number in E\.164 format\.  
Type: String  
Length: 1\-256

**Type**  
The endpoint type\. Currently, an endpoint can only be a telephone number\.  
Valid values: `TELEPHONE_NUMBER` 

## MediaStream<a name="MediaStream"></a>

Information about the media stream used on the contact\.

**Type**  
Type: MediaStreamType  
Valid value: AUDIO

## QueueInfo<a name="ctr-QueueInfo"></a>

Information about a queue\.

**ARN**  
The Amazon Resource Name of the queue\.  
Type: ARN

**DequeueTimestamp**  
The date and time the contact was removed from the queue\. Either the customer disconnected or the contact was connected to an agent\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**Duration**  
The difference in time, in whole seconds, between `EnqueueTimestamp` and `DequeueTimestamp`\.  
Type: Integer  
Min value: 0

**EnqueueTimestamp**  
The date and time the contact was added to the queue\.  
Type: String \(*yyyy*\-*mm*\-*dd*T*hh*:*mm*:*ss*Z\)

**Name**  
The name of the queue\.  
Type: String  
Length: 1\-256

## RecordingInfo<a name="ctr-RecordingInfo"></a>

Information about a recording\.

**DeletionReason**  
If the recording was deleted, this is the reason entered for the deletion\.  
Type: String

**Location**  
The location, in Amazon S3, for the recording\.  
Type: String  
Length: 0\-256

**Status**  
The recording status\.  
Valid values: `AVAILABLE` \| `DELETED` 

**Type**  
The recording type\.  
Valid values: `AUDIO` 

## RoutingProfile<a name="ctr-RoutingProfile"></a>

Information about a routing profile\.

**ARN**  
The Amazon Resource Name of the routing profile\.  
Type: ARN

**Name**  
The name of the routing profile\.  
Type: String  
Length: 1\-100