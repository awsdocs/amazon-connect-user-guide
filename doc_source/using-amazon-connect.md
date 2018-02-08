# Using Amazon Connect<a name="using-amazon-connect"></a>

This guide covers how to get started with using Amazon Connect to make and receive calls, generate helpful metrics and reporting, manage user permissions and security profiles, create contact flows, and scale your contact center to match your business requirements\.

## Amazon Connect Concepts<a name="amazon-connect-concepts"></a>

The terminology and concepts described below are central to your understanding and use of Amazon Connect\.

**instance**  
A container for the resources and settings of your contact center, including user directory, data encryption and storage settings, and integration settings\.

**Amazon Connect**  
The management console where configuration and reporting are managed\. Each instance has a separate management console\.

**Contact Control Panel \(CCP\)**  
The interface through which agents handle customer contacts\.

**Outbound caller ID**  
The name and number displayed to the recipient of a call as the ID of a caller\.  
When you create a queue, you can specify an **Outbound caller ID name** and **Outbound caller ID number** to use for the queue\. However, the information displayed to the person you call may not always match the name or number registered with the carrier for Amazon Connect\. In some cases, the caller ID information is provided by the carrier of the person you are calling\. The information may not be up\-to\-date with that carrier, or the number may get passed differently between systems due to hardware or configuration differences\. If that is the case, the person you call may not see the phone number, or may see the name of a previously registered owner of the number, instead of the name of the registered person from your organization\.

**agent**  
Users who handle contacts using Amazon Connect\.

**users**  
All users of the system and web application\. Users can have different roles or permissions, for example, agent, manager, or system administrator\.

**reports**  
Real\-time and historical reporting for an instance, including agent activity\.

**status**  
Metrics are gathered based on changes in agent status \(available, offline, and so on\)\. 