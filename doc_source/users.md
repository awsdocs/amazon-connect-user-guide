# Working with User Settings<a name="users"></a>

There are several roles and permissions available on Amazon Connect\. The varying levels of permission allow for protection of valuable data \(such as call records\), and the management of resources\.

Permissions also dictate which users can see various parts of Amazon Connect\. For example, an agent has view\-only access and is only able to see the CCP\. An administrator is able to see and access all the functionality in Amazon Connect\.

## Managing User Profiles and Permissions<a name="usermanagement"></a>

You can manage user security, routing, reporting, and contact management settings with granulated permissions and profiles\.

## Security Profiles<a name="securityprofiles"></a>

Permissions are required for users to access, view, and edit certain administrative functionality and tools\. Security profiles determine which users and roles can view and perform specific tasks\. The following resource groups can be edited:

+ **Routing**—Routing profiles, quick connects, hours of operation, queues\.

+ **Numbers and flows**—Prompts, contact flows, phone numbers\.

+ **Users and permissions**—Users, agent grouping, security profiles, agent status\.

+ **Contact Control Panel \(CCP\)**—CCP access, outbound calls\.

+ **Metrics and Quality**—Access metrics, manager listen in, call recordings, saved reports\.

+ **Historical Changes**—View historical changes\.

Security permissions for each group are further granulated to allow for different levels of permission, from allowing full read\-write access to **All** resources to only allowing a user to **View** resources\.

There are four default security profiles:

+ **Admin**—An admin can access and edit all available resources and actions\.

+ **Agent**—This profile only allows access to the CCP\. No other actions are available\.

+ **CallCenterManager**—This profile allows access to user management, metrics, and routing settings\.

+ **QualityAnalyst**—This profile only allows access to metrics\.

**To create a security profile**

1. Choose **Users**, **Security profiles**, **Add new security profile**\.

1. Type a name and description, and choose the appropriate permissions for each group\.
**Note**  
In some cases, selecting a permission results in other permissions being included\. For example, if you choose **Edit**, **View** is also included\.

1. Choose **Save**\.

**To manage and edit security profiles**

1. Choose **Users**, **Security profiles**, and select the profile to edit\.

1. Select a category name to display the options available\.

1. Select or deselect options as required\.

1. Choose **Save**\.

**To assign a security profile to a user**

1. Choose **Users**, **User management**\.

1. Select a single user \(or multiple users\) and choose **Edit**\.

1. Select the relevant profiles from the options provided\.
**Note**  
If you're editing multiple users, they are all assigned the chosen settings\.

1. Choose **Save**\.

## Routing Profiles<a name="routing-profiles"></a>

A routing profile is a collection of queues that determines how contacts are routed to agents\. Routing profiles are used to prioritize contacts across specific queues and manage the priority in which contacts are handled based on the queues they are routed to\. This can be used to ensure alignment with service SLAs\. Routing profiles are managed and assigned to agents by the administrator\. An agent can only be assigned a single routing profile at a time; however, they may serve multiple queues, based on rules defined in the routing profile\.

**To create a routing profile**

1. Choose **Users**, **Routing profiles**, **Add new profile**\.

1. Enter or choose the following information:

   + **Name**—A searchable display name\. 

   + **Description**—The routing profile's function\.

   + **Routing profile queues**—A queue to associate with the routing profile\. You can add multiple queues\.

   + **Priority**—The order in which contacts are handled by the queue they are in\. Set values in order of importance, with the lowest number equaling the highest priority\. For example, a contact in a queue with a priority of 2 would be a lower priority than a contact in a queue with a priority of 1\.

   + **Delay \(in seconds\)**—The minimum hold time before the call is routed to an agent with a matching queue/threshold combination\. 

   + **Default outbound queue**—Outbound calls must be associated with one of the associated queues\. 

1. Choose **Add new profile**\.

Here's an example of a profile:


| Queue | Priority | Delay \(in seconds\) | 
| --- | --- | --- | 
|  Premium Support 1  |  1  |  0  | 
|  Premium Support 2  |  1  |  0  | 
|  Premium Support 3  |  2  |  20  | 
|  Premium Support 4  |  3  |  80  | 

This profile prioritizes Premium Support 1 and Premium Support 2 equally \(because each has a priority 1\)\.

+ Agents with this profile may take calls for Premium Support 3 when customers for Premium Support 3 are waiting for 20 seconds or longer \(and no Premium Support 1 or Premium Support 2 calls are in queue\)\.

+ Agents with this profile may take calls for Premium Support 4 when customers for Premium Support 4 are waiting 80 seconds or longer \(and no calls for Premium Support 1, Premium Support 2 or Premium Support 3 are in queue\)\.