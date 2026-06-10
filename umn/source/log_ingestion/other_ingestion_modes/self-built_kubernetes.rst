:original_name: lts_04_1120.html

.. _lts_04_1120:

Self-Built Kubernetes
=====================

LTS can inject self-built Kubernetes application logs.

Prerequisites
-------------

-  Ensure that the Helm v3 installation command has been executed in the Kubernetes cluster.
-  Ensure that kubectl has been configured for the Kubernetes cluster.

Procedure
---------

Set the log access mode to **Self-built K8s - Application Logs**. If your Kubernetes cluster is in the cloud, perform the following steps to complete the access configuration.

#. Log in to the LTS console.

#. Choose **Log Ingestion** in the left navigation pane. On the page displayed, click **Self-Built Software** > **Self-built K8s - Application Logs**.

#. Select a log stream.

   Choose between **Fixed log stream** and **Custom log stream** to suite your requirements. You are recommended to use **Fixed log stream**.

   **Fixed log stream**

   Logs will be collected to a fixed log stream. The default log streams of CCE clusters: **stdout-**\ *{ClusterID}* for standard output/errors, **hostfile-**\ *{ClusterID}* for node files, **event-**\ *{ClusterID}* for Kubernetes events, and **containerfile-**\ *{ClusterID}* for container files. Log streams are automatically named with a cluster ID. For example, if the cluster ID is **Cluster01**, the standard output/error log stream is **stdout-Cluster01**.

   Log streams that can be created for a CCE cluster are **stdout-**\ *{ClusterID}* for standard output/errors, **hostfile-**\ *{ClusterID}* for node files, **event-**\ *{ClusterID}* for Kubernetes events, and **containerfile-**\ *{ClusterID}* for container files. If one of them has been created in a log group, the log stream will no longer be created in the same log group or other log groups.

   a. Select **Fixed log stream** for **Collect**.
   b. Enter the cluster name and ID.
   c. Select a log group.

      .. note::

         If there is no such group, the system displays the following message: **This log group does not exist and will be automatically created to start collecting logs.**

   d. Click **Next: Check Dependencies**.

   **Custom log stream**

   a. Select **Custom log stream**.
   b. Enter the cluster name and ID.
   c. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.
   d. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.
   e. Click **Next: Check Dependencies**.

#. Check dependencies.

   a. The system automatically checks whether the following are met:

      -  There is a host group with the custom identifier **k8s-log-**\ *ClusterID*.
      -  There is a log group named **k8s-log-**\ *ClusterID*. The log retention period and description of a log group can be modified.
      -  There is a recommended log stream. The log retention period and description of a log stream can be modified. If **Fixed log stream** is selected, this item is checked.

      You need to meet all the requirements before moving on. If not, click **Auto Correct**.

      .. note::

         -  **Auto Correct**: a one-click option to finish the previous settings.
         -  **Check Again**: Recheck dependencies.
         -  If **Custom log stream** is selected, the check item **There is a log group named k8s-log-ClusterID** is optional. Toggle the switch to enable or disable the check.

   b. Click **Next: Install ICAgent**.

#. Install the log collection component.

   In the Kubernetes cluster, perform the following steps on any host:

   a. Obtain the ICAgent installation package.

      -  Copy the decompression command on the LTS page to decompress the ICAgent installation package.

         .. code-block::

            tar -xzvf icagentK8s-5.5.1.2.tar.gz

      -  Run the following command to go to the **icagentK8s** directory:

         .. code-block::

            cd icagentK8s

      -  Generate installation commands.

         Select the region of ingested logs.

         Select the project ID of the ingesting account.

         For **Kubernetes Cluster**, select **In cloud**.

   b. Install ICAgent.

      #. Copy the ICAgent installation command.

         To prevent your AK/SK pair from being disclosed, select **Turn off command history to prevent the AK/SK from being stored** to disable historical record collection.

         The generated installation command is as follows (replace *x.x.x.x* with the actual IP address displayed on the page):

         .. code-block::

            set +o history; bash icagent_log_install.sh 2a473356cca5487f8373be891bffc1cf test-xx123456 region0_id {input_your_ak} {input_your_sk} x.x.x.x podlb

         To enter the AK/SK pair, either:

         1. Copy the command and replace *{input_your_ak}* and *{input_your_sk}* without the braces {}, or

         2. Run the copied command and enter the AK and SK when "Enter the AK" and "Enter the SK" are displayed.

      #. Use a remote login tool (such as PuTTY) to log in to the target host as the **root** user and run the copied command.

         If the message "ICAgent install success" is displayed, the installation is successful. Then choose **Host Management** in the navigation pane to check the ICAgent status.

   c. Click **ICAgent Already Installed**.

#. (Optional) Select a host group.

   a. Select one or more host groups from which you want to collect logs. If there are no desired host groups, click **Create** above the host group list to create one. For details, see :ref:`Creating a Host Group (Custom Identifier) <lts_02_1033__en-us_topic_0000001118763740_section6798040548>`.

      .. note::

         -  The host group to which the cluster belongs is selected by default. You can also select host groups as required.
         -  You can skip this step and configure host groups after the ingestion configuration is complete. There are two options to do this:

            -  On the LTS console, choose **Host Management** > **Host Groups** and associate host groups with ingestion configurations.
            -  On the LTS console, choose **Log Ingestion** in the navigation pane and click an ingestion configuration. On the displayed page, add one or more host groups for association.

   b. Click **Next: Configurations**.

#. Configure the collection.

   a. Specify collection rules. For details, see :ref:`Configuring the Collection <lts_04_1120__en-us_topic_0000001557535581_section1191613128141>`.
   b. Click **Next: Log Structuring**.

#. (Optional) Configure log structuring.

   a. Click **Skip** or perform structuring configurations. For details, see :ref:`Cloud Structuring Parsing <lts_0821>`.

      .. note::

         If structuring has been configured for the selected log stream, exercise caution when deleting it.

   b. Click **Next: Index Settings**.

#. (Optional) Configure **Index Settings**.

   a. Click **Skip and Submit** or configure indexing. For details, see :ref:`Index Settings <lts_05_0008>`.
   b. Click **Submit**.

#. The ingestion configuration is complete.

.. _lts_04_1120__en-us_topic_0000001557535581_section1191613128141:

Configuring the Collection
--------------------------

When you configure log ingestion for self-built Kubernetes clusters, the collection configuration details are as follows.

#. **Basic Settings**: Enter a name containing 1 to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. The name cannot start with a period or underscore, or end with a period.
#. **Data Source**: Select a data source type and configure it.

   -  **Container standard output**: Collects stderr and stdout logs of a specified container in the cluster.

      .. note::

         -  The standard output of the matched container is collected to the specified log stream. Standard output to AOM stops.
         -  The container standard output must be unique to a host.

   -  **Container file**: Collects file logs of a specified container in the cluster.
   -  **Node file**: Collects files of a specified node in the cluster.

      .. note::

         You cannot add the same host path to more than one log stream.

   -  **Kubernetes event**: Collects event logs in the Kubernetes cluster.

      .. note::

         Kubernetes events of a Kubernetes cluster can be ingested to only one log stream.

   .. table:: **Table 1** Collection configuration parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Container standard output         | Collects stderr and stdout logs of a specified container in the cluster. Either **Container Standard Output (stdout)** or **Container Standard Error (stderr)** must be enabled.                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container file                    | -  :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`: Specify the paths from which LTS will collect logs.                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    .. note::                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       -  If a container mount path has been configured for the CCE cluster workload, the paths added for this field are invalid. The collection paths take effect only after the mount path is deleted. |
      |                                   |       -  You cannot add the same host path to more than one log stream.                                                                                                                                 |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **Set Collection Filters**: Blacklisted directories or files will not be collected. If you specify a directory, all files in the directory are filtered out.                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Node file                         | -  :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`: Specify the paths from which LTS will collect logs.                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   |    .. note::                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                         |
      |                                   |       You cannot add the same host path to more than one log stream.                                                                                                                                    |
      |                                   |                                                                                                                                                                                                         |
      |                                   | -  **Set Collection Filters**: Blacklisted directories or files will not be collected. If you specify a directory, all files in the directory are filtered out.                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Kubernetes event                  | You do not need to configure this parameter. Only ICAgent 5.12.130 and later versions are supported.                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. **Kubernetes Matching Rules**: Set these parameters only when the data source type is set to **Container standard output** or **Container file**.

   .. note::

      After entering a regular expression matching rule, click the button of verification to verify the regular expression.

   .. table:: **Table 2** Kubernetes matching rules

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Namespace Name Regular Expression | Specifies the container whose logs are to be collected based on the namespace name. Regular expression matching is supported.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will collect logs of the namespaces with names matching this expression. To collect logs of all namespaces, leave this field empty.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Pod Name Regular Expression       | Specifies the container whose logs are to be collected based on the pod name. Regular expression matching is supported.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will collect logs of the pods with names matching this expression. To collect logs of all pods, leave this field empty.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Name Regular Expression | Specifies the container whose logs are to be collected based on the container name (the Kubernetes container name is defined in **spec.containers**). Regular expression matching is supported.                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will collect logs of the containers with names matching this expression. To collect logs of all containers, leave this field empty.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Label Whitelist         | Specifies the containers whose logs are to be collected. If you want to set a container label whitelist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will match all containers with a container label containing a specified **Label Key** with an empty corresponding **Label Value**. If **Label Value** is not empty, only containers with a container label containing a specified **Label Key** that is equal to its **Label Value** are matched with LTS. **Label Key** requires full matching while **Label Value** supports regular matching. The relationship between multiple whitelists is based on an OR operation, meaning that a container label can be matched as long as it meets any of the whitelists. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Label Blacklist         | Specifies the containers whose logs are not to be collected. If you want to set a container label blacklist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will exclude all containers with a container label containing a specified **Label Key** with an empty corresponding **Label Value**. If **Label Value** is not empty, only containers with a container label containing a specified **Label Key** that is equal to its **Label Value** will be excluded. **Label Key** requires full matching while **Label Value** supports regular matching. The relationship between multiple blacklists is based on an OR operation, meaning that a container label can be excluded as long as it meets any of the blacklists.  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Label                   | After the **Container Label** is set, LTS adds related fields to logs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS adds the specified fields to the log when each **Label Key** has a corresponding **Label Value**. For example, if you enter **app** as the key and **app_alias** as the value, when the container label contains **app=lts**, **{app_alias: lts}** will be added to the log.                                                                                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment Variable Whitelist    | Specifies the containers whose logs are to be collected. If you want to set an environment variable whitelist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will match all containers with environment variables containing either an **Environment Variable Key** with an empty corresponding **Environment Variable Value**, or an **Environment Variable Key** with its corresponding **Environment Variable Value**. **Label Key** requires full matching while **Label Value** supports regular matching. The relationship between multiple whitelists is based on an OR operation, meaning that a container environment variable can be matched as long as it meets any of key-value pairs.                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment Variable Blacklist    | Specifies the containers whose logs are not to be collected. If you want to set an environment variable blacklist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS will exclude all containers with environment variables containing either an **Environment Variable Key** with an empty corresponding **Environment Variable Value**, or an **Environment Variable Key** with its corresponding **Environment Variable Value**. **Label Key** requires full matching while **Label Value** supports regular matching. The relationship between multiple blacklists is based on an OR operation, meaning that a container environment variable can be excluded as long as it meets any of key-value pairs.                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment Variable Label        | After the environment variable label is set, the log service adds related fields to the log.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    LTS adds the specified fields to the log when each **Environment Variable Key** has a corresponding **Environment Variable Value**. For example, if you enter "app" as the key and "app_alias" as the value, when the Kubernetes environment variable contains "app=lts", "{app_alias: lts}" will be added to the log.                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Perform other configurations.

   .. table:: **Table 3** Other configurations

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================+
      | Split Logs                        | LTS supports log splitting, which is disabled by default.                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                   |
      |                                   | If this option is enabled, a single-line log larger than 500 KB will be split into multiple lines for collection. For example, a 600 KB single-line log will be split into a line of 500 KB and a line of 100 KB. |
      |                                   |                                                                                                                                                                                                                   |
      |                                   | If this option is disabled, when a log exceeds 500 KB, the extra part will be truncated and discarded.                                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Collect Binary Files              | LTS supports binary file collection, which is disabled by default.                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                   |
      |                                   | Run the **file -i** *File_name* command to view the file type. **charset=binary** indicates that a log file is a binary file.                                                                                     |
      |                                   |                                                                                                                                                                                                                   |
      |                                   | If this option is enabled, binary log files will be collected, but only UTF-8 strings are supported. Other strings will be garbled on the LTS console.                                                            |
      |                                   |                                                                                                                                                                                                                   |
      |                                   | If this option is disabled, binary log files will not be collected.                                                                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Configure the log format and log time.

   .. table:: **Table 4** Log collection settings

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================+
      | Log Format                        | -  **Single-line**: Each log line is displayed as a single log event.                                                                                                                                                                                       |
      |                                   | -  **Multi-line**: Multiple lines of exception log events can be displayed as a single log event. This is helpful when you check logs to locate problems.                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Time                          | **System time**: log collection time by default. It is displayed at the beginning of each log event.                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    -  Log collection time is the time when logs are collected and sent by ICAgent to LTS.                                                                                                                                                                   |
      |                                   |    -  Log printing time is the time when logs are printed. ICAgent collects and sends logs to LTS with an interval of 1 second.                                                                                                                             |
      |                                   |    -  Restriction on log collection time: Logs are collected within 24 hours before and after the system time.                                                                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                   | **Time wildcard**: You can set a time wildcard so that ICAgent will look for the log printing time as the beginning of a log event.                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | -  If the time format in a log event is **2019-01-01 23:59:59.011**, the time wildcard should be set to **YYYY-MM-DD hh:mm:ss.SSS**.                                                                                                                        |
      |                                   | -  If the time format in a log event is **19-1-1 23:59:59.011**, the time wildcard should be set to **YY-M-D hh:mm:ss.SSS**.                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    If a log event does not contain year information, ICAgent regards it as printed in the current year.                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | Example:                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. code-block::                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    YY   - year (19)                                                                                                                                                                                                                                         |
      |                                   |    YYYY - year (2019)                                                                                                                                                                                                                                       |
      |                                   |    M    - month (1)                                                                                                                                                                                                                                         |
      |                                   |    MM   - month (01)                                                                                                                                                                                                                                        |
      |                                   |    D    - day (1)                                                                                                                                                                                                                                           |
      |                                   |    DD   - day (01)                                                                                                                                                                                                                                          |
      |                                   |    hh   - hours (23)                                                                                                                                                                                                                                        |
      |                                   |    mm   - minutes (59)                                                                                                                                                                                                                                      |
      |                                   |    ss   - seconds (59)                                                                                                                                                                                                                                      |
      |                                   |    SSS  - millisecond (999)                                                                                                                                                                                                                                 |
      |                                   |    hpm     - hours (03PM)                                                                                                                                                                                                                                   |
      |                                   |    h:mmpm    - hours:minutes (03:04PM)                                                                                                                                                                                                                      |
      |                                   |    h:mm:sspm  - hours:minutes:seconds (03:04:05PM)                                                                                                                                                                                                          |
      |                                   |    hh:mm:ss ZZZZ (16:05:06 +0100)                                                                                                                                                                                                                           |
      |                                   |    hh:mm:ss ZZZ  (16:05:06 CET)                                                                                                                                                                                                                             |
      |                                   |    hh:mm:ss ZZ   (16:05:06 +01:00)                                                                                                                                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Segmentation                  | This parameter needs to be specified if the **Log Format** is set to **Multi-line**. **By generation time** indicates that a time wildcard is used to detect log boundaries, whereas **By regular expression** indicates that a regular expression is used. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Regular Expression                | You can set a regular expression to look for a specific pattern to indicate the beginning of a log event. This parameter needs to be specified when you select **Multi-line** for **Log Format** and **By regular expression** for **Log Segmentation**.    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The time wildcard and regular expression will look for the specified pattern right from the beginning of each log line. If no match is found, the system time, which may be different from the time in the log event, is used. In general cases, you are advised to select **Single-line** for **Log Format** and **System time** for **Log Time**.
