:original_name: lts_04_1031.html

.. _lts_04_1031:

Collecting Logs from ECS
========================

ICAgent collects logs from hosts based on your specified collection rules, and packages and sends the collected log data to LTS on a log stream basis. You can view logs on the LTS console in real time.

Prerequisites
-------------

ICAgent has been :ref:`installed <lts_02_0013>` and :ref:`added <lts_02_1033__en-us_topic_0000001118763740_li682633315215>` to the host group.

.. _lts_04_1031__en-us_topic_0000001118501736_section7819102916332:

Procedure
---------

Perform the following operations to configure ECS log ingestion:

#. Log in to the LTS console.

#. In the navigation pane on the left, choose **Log Ingestion** and click **ECS (Elastic Cloud Server)**.

#. Select a log stream.

   a. Select a log group from the drop-down list of **Log Group**. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the drop-down list of **Log Stream**. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: Select Host Group**.

#. Select host groups.

   a. In the host group list, select one or more host groups to collect logs. If there are no desired host groups, click **Create** in the upper left corner of the list. On the displayed **Create Host Group** page, create a host group. For details, see :ref:`Creating a Host Group (IP Address) <lts_02_1033__en-us_topic_0000001118763740_section665755611241>`.

      .. note::

         You can skip this step and configure host groups after the ingestion configuration is complete. There are two ways to do this:

         -  Choose **Host Management** in the navigation pane, click **Host Groups**, and associate host groups with ingestion configurations.
         -  Choose **Log Ingestion** in the navigation pane, click an ingestion configuration, and make the association on the details page.

   b. Click **Next: Configurations**.

#. Configure the collection.

   Specify collection rules. For details, see :ref:`Configuring the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`.

#. Click **Back to Ingestion Configurations** to :ref:`check the ingestion details <lts_04_1031__en-us_topic_0000001118501736_section16196351114917>`. You can also click **View Log Stream** to view the log stream to which logs are ingested.

.. _lts_04_1031__en-us_topic_0000001118501736_section196913102330:

Configuring the Collection
--------------------------

When you configure host log ingestion, the configuration details are as follows.

#. **Collection Configuration Name**: Enter up to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. The name cannot start with a period or underscore, or end with a period.

   .. note::

      To import old-edition ingestion configurations to the new edition of log ingestion, click **Import Old-Edition Configuration**.

      -  If LTS is newly installed and **Import Old-Edition Configuration** is not displayed, you can directly create a configuration without importing the old one.
      -  If LTS is upgraded, **Import Old-Edition Configuration** is displayed. If you need the host log path in the old configuration, import the old configuration or create one.

#. .. _lts_04_1031__en-us_topic_0000001118501736_li17754123317308:

   **Collection Paths**: Add one or more host paths. LTS will collect logs from these paths.

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

#. **Set Collection Filters**: Blacklisted directories or files will not be collected. If you specify a directory, all files in the directory are filtered out.

   Blacklist filters can be exact matches or wildcard pattern matches. For details, see :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`.

   .. note::

      If you blacklist a file or directory that has been set as a collection path in the previous step, the blacklist settings will be used and the file or files in the directory will be filtered out.

#. Configure the log format and log time.

   .. table:: **Table 1** Log collection settings

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
-  To modify an ingestion configuration, click |image1| in the **Operation** column for the target configuration and modify the configuration by referring to :ref:`Procedure <lts_04_1031__en-us_topic_0000001118501736_section7819102916332>`.
-  To delete an ingestion configuration, click |image2| in the **Operation** column for the target configuration. You can also select more than one ingestion configurations and click **Delete** above the configuration list to delete them at a go.
-  Tag management: Click |image3| in the **Operation** column of the row that contains the desired ingestion configuration to add a tag.

.. |image1| image:: /_static/images/en-us_image_0000001123555094.png
.. |image2| image:: /_static/images/en-us_image_0000001123715432.png
.. |image3| image:: /_static/images/en-us_image_0000001499855785.png
