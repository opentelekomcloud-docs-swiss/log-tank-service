:original_name: lts_04_1031.html

.. _lts_04_1031:

Collecting Logs from ECS
========================

ICAgent collects logs from Elastic Cloud Servers (ECSs) based on your specified collection rules, and packages and sends the collected log data to LTS on a log stream basis. You can view logs on the LTS console in real time.

Prerequisites
-------------

ICAgent has been :ref:`installed <lts_02_0013>` and :ref:`added <lts_02_1033__en-us_topic_0000001118763740_li682633315215>` to the host group.

Procedure
---------

Perform the following operations to configure ECS log ingestion:

#. Log in to the LTS console.

#. In the left navigation pane, choose **Log Ingestion**. On the displayed page, click **ECS (Elastic Cloud Server)**.

#. Select a log group.

   a. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: (Optional) Select Host Group**.

#. Select a host group.

   a. Select one or more host groups from which you want to collect logs. If there are no desired host groups, click **Create** above the host group list to create one. For details, see :ref:`Creating a Host Group (IP Address) <lts_02_1033__en-us_topic_0000001118763740_section665755611241>`.

      .. note::

         You can also deselect the host group. In this case, the collection configuration does not take effect. You are advised to select a host group during the first ingestion. You can skip this step and configure host groups after the ingestion configuration is complete. There are two options to do this:

         -  On the LTS console, choose **Host Management** > **Host Groups** and associate host groups with ingestion configurations.
         -  On the LTS console, choose **Log Ingestion** in the navigation pane and click an ingestion configuration. On the displayed page, add one or more host groups for association.

   b. Click **Next: Configure Collection**.

#. Configure the collection.

   Specify collection rules. For details, see :ref:`Configurations <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`.

#. (Optional) Configure log structuring.

   For details, see :ref:`Cloud Structuring Parsing <lts_0821>`.

   .. note::

      If structuring has been configured for the selected log stream, exercise caution when deleting it.

#. (Optional) Configure **Index Settings**.

   For details, see :ref:`Index Settings <lts_05_0008>`.

#. Click **Submit**. After the ingestion is successful, click **Back to Ingestion Configurations** to :ref:`check the ingestion details <lts_04_1031__en-us_topic_0000001118501736_section16196351114917>`. You can also click **View Log Stream** to view the log stream to which logs are ingested.

.. _lts_04_1031__en-us_topic_0000001118501736_section196913102330:

Configurations
--------------

When you configure host log ingestion, the collection configuration details are as follows.

#. **Collection Configuration Name**: Enter up to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. The name cannot start with a period or underscore, or end with a period.

   .. note::

      **Import Old-Edition Configuration**: Import the host ingestion configuration of the old version to the log ingestion of the new version.

      -  If LTS is newly installed and **Import Old-Edition Configuration** is not displayed, you can directly create a configuration without importing the old one.
      -  If LTS is upgraded, **Import Old-Edition Configuration** is displayed. If you need the host log path in the old configuration, import the old configuration or create one.

#. .. _lts_04_1031__en-us_topic_0000001118501736_li17754123317308:

   **Collection Paths**: Specify the paths from which LTS will collect logs.

   -  Logs can be collected recursively. A double asterisk (**) can represent up to 5 directory levels in a path.

      For example, **/var/logs/**/a.log** matches the following logs:

      .. code-block::

         /var/logs/1/a.log
         /var/logs/1/2/a.log
         /var/logs/1/2/3/a.log
         /var/logs/1/2/3/4/a.log
         /var/logs/1/2/3/4/5/a.log

      .. note::

         -  **/1/2/3/4/5/** indicates the 5 levels of directories under the **/var/logs** directory. All the **a.log** files found in all these levels of directories will be collected.
         -  Only one double asterisk (**) can be contained in a collection path. For example, **/var/logs/**/a.log** is acceptable but **/opt/test/**/log/*\*** is not.
         -  A collection path cannot begin with a double asterisk (**), such as **/**/test** to avoid collecting system files.

   -  You can use an asterisk (*) as a wildcard for fuzzy match. The wildcard (*) can represent one or more characters of a directory or file name.

      .. note::

         If a log collection path is similar to **C:\\windows\\system32** but logs cannot be collected, enable the Web Application Firewall (WAF) and configure the path again.

      -  Example 1: **/var/logs/*/a.log** will match all **a.log** files found in all directories under the **/var/logs/** directory:

         /var/logs/1/a.log

         /var/logs/2/a.log

      -  Example 2: **/var/logs/service-*/a.log** will match files as follows:

         /var/logs/service-1/a.log

         /var/logs/service-2/a.log

      -  Example 3: **/var/logs/service/a*.log** will match files as follows:

         /var/logs/service/a1.log

         /var/logs/service/a2.log

   -  If the collection path is set to a directory (such as **/var/logs/**), only **.log**, **.trace**, and **.out** files in the directory are collected.

      If the collection path is set to a file name, the corresponding file is collected. Only text files can be collected. To query the file format, run **file -i** *File name*.

   .. note::

      -  Ensure that sensitive information is not collected.
      -  It only collects logs of ECS (host) instances.
      -  A collection path can be configured only once. It means that a path of a host cannot be added for different log streams. Otherwise, log collection may be abnormal.
      -  If a collection path of a host has been configured in AOM, do not configure the path in LTS. If a path is configured in both AOM and LTS, only the path that is configured later takes effect.
      -  If log files were last modified more than 12 hours earlier than the time when the path is added, the files are not collected.

#. **Set Collection Filters**: Blacklisted directories or files will not be collected. If you specify a directory, all files in the directory are filtered out, but log files in the folders in the directory cannot be filtered out.

   Blacklist filters can be exact matches or wildcard pattern matches. For details, see :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`.

   .. note::

      -  If you blacklist a file or directory that has been set as a collection path in the previous step, the blacklist settings will be used and the file or files in the directory will be filtered out.
      -  If a log has been added to the blacklist, it cannot be collected even if you create a log ingestion task. You can collect it again only after you delete the collection path from the blacklist.

#. Perform other configurations.

   .. table:: **Table 1** Other configurations

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

   .. table:: **Table 2** Log collection settings

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
      |                                   |    SSS - millisecond (999)                                                                                                                                                                                                                                  |
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

.. _lts_04_1031__en-us_topic_0000001118501736_section16196351114917:

Checking Ingestion Configurations
---------------------------------

On the LTS console, choose **Log Ingestion** in the navigation pane. Alternatively, access the **Log Ingestion** page by clicking **Back to Ingestion Configurations** when you finish configuring log ingestion.

-  All ingestion configurations are displayed on the **Log Ingestion** page. Click an ingestion configuration to view its details.
-  Click the name of the log group or log stream on the row that contains an ingestion configuration to check the log group or log stream details.
-  The **Operation** column in the ingestion configuration list provides buttons for you to copy, modify, delete, and manage tags.
