:original_name: lts_04_0015.html

.. _lts_04_0015:

Collecting Logs from Hosts
==========================

ICAgent collects logs from a host based on your specified collection rules, and packages and sends the collected log data to LTS on a log-stream basis. You can view logs on the LTS console in real time.

Prerequisites
-------------

-  You have created a log group.
-  You have created a log stream.
-  You have installed ICAgent.

Procedure
---------

#. Log in to the LTS console and choose **Log Management** in the navigation pane.

#. In the log group list on the **Log Management** page, click the name of the target log group.

#. In the log stream list, click the name of the target log stream.

#. In the navigation pane, choose **Collection Configuration**. Then, click **Add Path**.


   .. figure:: /_static/images/en-us_image_0000001904389432.png
      :alt: **Figure 1** Configuring the collection

      **Figure 1** Configuring the collection

#. In the **Add Host** step, select the host whose logs you want to collect and click **Next**.

#. Add the path of logs you want to collect.

   -  Logs can be collected recursively. A double asterisk (**) can represent up to 5 directory levels.

      For example, **/var/logs/**/a.log** will match the following logs:

      .. code-block::

         /var/logs/1/a.log
         /var/logs/1/2/a.log
         /var/logs/1/2/3/a.log
         /var/logs/1/2/3/4/a.log
         /var/logs/1/2/3/4/5/a.log

      .. note::

         -  **/1/2/3/4/5/** indicates directories of 5 levels under the **/var/logs** directory. All the **a.log** files found in all these directories will be collected.
         -  Only one double asterisk (**) can be contained in a collection path. For example, **/var/logs/**/a.log** is acceptable but **/opt/test/**/log/*\*** is not.
         -  A collection path cannot begin with a double asterisk (**), such as **/**/test**, because that path could include system files.

   -  You can use an asterisk (*) as a wildcard for fuzzy match. The wildcard (*) can represent one or more characters of a directory or file name.

      -  Example 1: **/var/logs/*/a.log** will return:

         /var/logs/1/a.log

         /var/logs/2/a.log

      -  Example 2: **/var/logs/service-*/a.log** will return:

         /var/logs/service-1/a.log

         /var/logs/service-2/a.log

      -  Example 3: **/var/logs/service/a*.log** will return:

         /var/logs/service/a1.log

         /var/logs/service/a2.log

   -  If the collection path is set to a directory (such as **/var/logs/**), the .log, .trace, and .out files in the current directory and subdirectories up to two levels down are collected.

      If the collection path is set to a file name, the corresponding file is collected. Note that only text files can be collected.

   .. note::

      -  Ensure that sensitive information is not collected.
      -  LTS cannot collect logs of PostgreSQL (database) instances. It only collects logs of ECS (host) instances.
      -  A collection path can be configured only once. It means that a path of a host cannot be added for different log streams. Otherwise, log collection may be abnormal.
      -  If a collection path of a host has been configured in AOM, do not configure the path in LTS. If a path is configured in both AOM and LTS, only the path that is configured later takes effect.
      -  If log files were last modified more than 12 hours earlier than the time when the path is added, the files are not collected.

#. Click **Next** to proceed to the **Set Collection Rule** stage.

   .. table:: **Table 1** Parameters for log collection rules

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
      |                                   |    Log collection time: when logs are collected and sent by ICAgent to LTS. Log printing time: when logs are printed.                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    ICAgent collects and sends logs to LTS in real time.                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                   | **Time wildcard**: You can set a time wildcard so that ICAgent will look for the log printing time as the beginning of a log event.                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | -  If the time format in a log event is **2019-01-01 23:59:59**, the time wildcard should be set to **YYYY-MM-DD hh:mm:ss**.                                                                                                                                |
      |                                   | -  If the time format in a log event is **19-1-1 23:59:59**, the time wildcard should be set to **YY-M-D hh:mm:ss**.                                                                                                                                        |
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

#. Click **OK**. LTS will collect logs based on your specified collection rules.

   You can reconfigure the log collection rules after the path is added.
