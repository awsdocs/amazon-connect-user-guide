# Using Amazon Connect<a name="using-amazon-connect"></a>

This guide covers how to configure your Amazon Connect instance to make and receive calls, generate helpful metrics and reporting, manage user permissions and security profiles, create contact flows, and use the Contact Control Panel \(CCP\) to handle calls\.

## Amazon Connect Concepts<a name="amazon-connect-concepts"></a>

The terminology and concepts described in this section help you become familiar with Amazon Connect\.

**Instance**  
An Amazon Connect instance is a container that holds all of the settings, data, and artifacts that comprise your contact center, such as the settings for identity management\. You modify instance settings to change the features enabled for your contact center, such as contact flow logging or data streaming\.  
You modify settings within Amazon Connect after you log in to your Amazon Connect instance to manage users, security profiles for access to Amazon Connect features, and how interactions with customers are handled in your contact center\.

**Contact**  
An interaction between a customer and your contact center\. Each contact is assigned a contact ID that you can use to track contacts through your contact center\. Most metrics and reports in Amazon Connect are associated with or related to contacts\.

**Contact Control Panel \(CCP\)**  
The client interface through which agents handle customer contacts\.

**Users**  
A user account in Amazon Connect that defines the information for a person to log in to and use Amazon Connect, such as user name, password, first name, and last name\. Users are granted permission to Amazon Connect features and resources by assigning a security profile to their user account\.

**Agent**  
A type of user in Amazon Connect that typically handles interactions with customers\. A user is an agent when their account is assigned the Agent security profile\.

**Reports**  
Real\-time and historical reports about your contact center, including metrics, contacts, and agents\.

**Outbound caller ID**  
The name and number displayed to the recipient of a call as the ID of a caller\.  
When you create a queue, you can specify an **Outbound caller ID name** and **Outbound caller ID number** to use for the queue\. However, the information displayed to the person you call may not always match the name or number registered with the carrier for Amazon Connect\. In some cases, the caller ID information is provided by the carrier of the person you are calling\. The information may not be up\-to\-date with that carrier, or the number may get passed differently between systems due to hardware or configuration differences\. If that is the case, the person you call may not see the phone number, or may see the name of a previously registered owner of the number, instead of the name of the registered person from your organization\.