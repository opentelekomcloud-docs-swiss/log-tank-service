:original_name: lts-03205.html

.. _lts-03205:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your LTS resources, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your LTS resources.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to the users to control their access to LTS resources. For example, some software developers in your enterprise need to use LTS resources but should not delete them or perform other high-risk operations. In this case, you can create IAM users for the software developers and grant them only the permissions required.

If your account does not need individual IAM users for permissions management, you may skip over this section.

IAM can be used for free. You pay only for the resources in your account. For more information about IAM, see the "Service Overview" in the *Identity and Access Management User Guide*.

LTS Permissions
---------------

By default, new IAM users do not have permissions assigned. You need to add users to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

LTS is a project-level service deployed and accessed in specific physical regions. When you set **Scope** to **Region-specific projects** and select the specified projects in the specified regions, the users only have permissions for LTS in the selected projects. If you select **All projects**, the users have permissions for LTS in all region-specific projects. When accessing LTS, the users need to switch to a region where they have been authorized to use LTS.

Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant Elastic Cloud Server (ECS) users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs.

:ref:`Table 1 <lts-03205__en-us_topic_0180792016_table7749356973>` lists all the system permissions of LTS.

.. _lts-03205__en-us_topic_0180792016_table7749356973:

.. table:: **Table 1** LTS system permissions

   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+
   | Name               | Description                                                                           | Type                  | Dependency                                                                         |
   +====================+=======================================================================================+=======================+====================================================================================+
   | LTS FullAccess     | Full permissions for LTS. Users with these permissions can perform operations on LTS. | System-defined policy | CCE Administrator, OBS Administrator, and AOM FullAccess                           |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+
   | LTS ReadOnlyAccess | Read-only permissions for LTS. Users with these permissions can only view LTS data.   | System-defined policy |                                                                                    |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+
   | LTS Administrator  | Administrator permissions for LTS.                                                    | System-defined role   | This role is dependent on the **Tenant Guest** and **Tenant Administrator** roles. |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+

:ref:`Table 2 <lts-03205__en-us_topic_0180792016_table121207991710>` lists the common operations supported by each system-defined policy and role of LTS. Choose the appropriate policies and roles as required.

.. _lts-03205__en-us_topic_0180792016_table121207991710:

.. table:: **Table 2** Common operations supported by each LTS system policy or role

   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Operation                                     | LTS FullAccess | LTS ReadOnlyAccess | LTS Administrator |
   +===============================================+================+====================+===================+
   | Querying a log group                          | Y              | Y                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Creating a log group                          | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Modifying a log group                         | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Deleting a log group                          | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Querying a log stream                         | Y              | Y                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Creating a log stream                         | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Modifying a log stream                        | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Deleting a log stream                         | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Configuring log collection from hosts         | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Querying the configuration of log structuring | Y              | Y                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Configuring log structuring                   | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Enabling quick analysis                       | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Disabling quick analysis                      | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Querying a filter                             | Y              | Y                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Disabling a filter                            | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Enabling a filter                             | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Deleting a filter                             | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Viewing a log transfer task                   | Y              | Y                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Creating a log transfer task                  | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Modifying a log transfer task                 | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Deleting a log transfer task                  | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Enabling a log transfer task                  | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Disabling a log transfer task                 | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Installing ICAgent                            | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Upgrading ICAgent                             | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+
   | Uninstalling ICAgent                          | Y              | x                  | Y                 |
   +-----------------------------------------------+----------------+--------------------+-------------------+

To use a custom fine-grained policy, log in to IAM as the administrator and select fine-grained permissions of LTS as required.

:ref:`Table 3 <lts-03205__en-us_topic_0180792016_table1643135052013>` describes fine-grained permission dependencies of LTS.

.. _lts-03205__en-us_topic_0180792016_table1643135052013:

.. table:: **Table 3** Fine-grained permission dependencies of LTS

   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | Permission                        | Description                                                 | Dependency                            |
   +===================================+=============================================================+=======================================+
   | lts:agents:list                   | List agents                                                 | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:buckets:get                   | Query a specified bucket                                    | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:groups:put                    | Modify a specified log group                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:transfers:create              | Create a log transfer task                                  | obs:bucket:PutBucketAcl               |
   |                                   |                                                             |                                       |
   |                                   |                                                             | obs:bucket:GetBucketAcl               |
   |                                   |                                                             |                                       |
   |                                   |                                                             | obs:bucket:GetEncryptionConfiguration |
   |                                   |                                                             |                                       |
   |                                   |                                                             | obs:bucket:HeadBucket                 |
   |                                   |                                                             |                                       |
   |                                   |                                                             | dis:streams:list                      |
   |                                   |                                                             |                                       |
   |                                   |                                                             | dis:streamPolicies:list               |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:groups:get                    | Query a specified log group                                 | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:groups:create                 | Creating a log group                                        | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:transfers:put                 | Modify a log transfer task                                  | obs:bucket:PutBucketAcl               |
   |                                   |                                                             |                                       |
   |                                   |                                                             | obs:bucket:GetBucketAcl               |
   |                                   |                                                             |                                       |
   |                                   |                                                             | obs:bucket:GetEncryptionConfiguration |
   |                                   |                                                             |                                       |
   |                                   |                                                             | obs:bucket:HeadBucket                 |
   |                                   |                                                             |                                       |
   |                                   |                                                             | dis:streams:list                      |
   |                                   |                                                             |                                       |
   |                                   |                                                             | dis:streamPolicies:list               |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:ecsOsLogPaths:list            | List OS log paths of a specified image                      | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentsConf:get                | Query a specified agent configuration                       | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logIndex:list                 | List log indexes                                            | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:transfers:delete              | Delete a log transfer task                                  | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:regex:create                  | Extract structured fields                                   | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:subscriptions:delete          | Delete a specified subscription                             | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:overviewLogsLast:list         | List the latest logs of a user                              | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logIndex:get                  | Query a specified log index                                 | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentsConf:create             | Create an agent configuration                               | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:datasources:batchdelete       | Batch delete data sources                                   | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:groups:list                   | List log groups                                             | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:transfers:action              | Enable or disable a log transfer task                       | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:datasources:post              | Create a data source                                        | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:topics:create                 | Create a log topic                                          | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:resourceTags:get              | Query resource tags                                         | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:filters:put                   | Modify a log filter                                         | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logs:list                     | List logs                                                   | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:subscriptions:create          | Create a subscription                                       | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:filtersAction:put             | Enable or disable a log filter                              | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:overviewLogsTopTopic:get      | Query data metrics of the topic with the largest log volume | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:datasources:put               | Modify a data source                                        | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logIndex:delete               | Delete a specified log index                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:filters:get                   | Query a specified log filter                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:topics:delete                 | Delete log topics                                           | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentSupportedOsLogPaths:list | List the log paths of OS supported by the agent             | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:topics:put                    | Modify a log topic                                          | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentHeartbeat:post           | Upload agent heartbeats                                     | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logsByName:upload             | Upload logs by log group name and topic name                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:buckets:list                  | List buckets                                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logIndex:post                 | Create a log index                                          | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logContext:list               | List log contexts                                           | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:groups:delete                 | Delete a specified log group                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:filters:delete                | Delete a log filter                                         | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:resourceTags:put              | Update resource tags                                        | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:overviewLogTotal:get          | Query the total log volume of the current user              | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:subscriptions:put             | Modify a specified subscription                             | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:subscriptions:list            | List subscriptions                                          | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:datasources:delete            | Delete a specified data source                              | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:transfersStatus:get           | Query the log transfer status                               | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logIndex:put                  | Modify a specified log index                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logs:upload                   | Upload logs                                                 | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentDetails:list             | List agent diagnostic logs                                  | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentsConf:put                | Modify an agent configuration                               | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:logstreams:list               | Filter log stream resources                                 | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:subscriptions:get             | Query a specified subscription                              | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:disStreams:list               | List DIS streams                                            | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:groupTopics:put               | Create a log group and topic                                | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:resourceInstance:list         | List resource instances                                     | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:transfers:list                | List transfer tasks                                         | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:topics:get                    | Query a specified log topic                                 | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentsConf:delete             | Delete a specified agent configuration                      | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:agentEcs:list                 | List ECSs                                                   | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:indiceLogs:list               | Search for logs                                             | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
   | lts:topics:list                   | List log topics                                             | None                                  |
   +-----------------------------------+-------------------------------------------------------------+---------------------------------------+
