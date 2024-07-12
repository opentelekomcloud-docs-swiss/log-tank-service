:original_name: lts_01_0013.html

.. _lts_01_0013:

Searching for Logs by Keyword
=============================

.. _lts_01_0013__section118029111411:

Search Syntax and Examples
--------------------------

:ref:`Table 1 <lts_01_0013__table973553521214>` describes the search syntax.

.. _lts_01_0013__table973553521214:

.. table:: **Table 1** Search syntax

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Filter                            | Description                                                                                                                                 |
   +===================================+=============================================================================================================================================+
   | Exact search by keyword           | Enter a keyword (case-sensitive) for exact search. A keyword is the word between two adjacent delimiters.                                   |
   |                                   |                                                                                                                                             |
   |                                   | You can enclose a keyword with wildcards (``*``), for example, **\*error\*** to tell LTS to return results that match your keyword exactly. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Exact search by phrase            | Enter a phrase (case-sensitive) for exact search.                                                                                           |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | &&                                | Intersection of search results.                                                                                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | \|\|                              | Union of search results.                                                                                                                    |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | AND                               | Intersection of search results                                                                                                              |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | OR                                | Union of search results                                                                                                                     |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | NOT                               | Results that satisfy **query1** but not **query2**                                                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | \*                                | Fuzzy search. The wildcard (``*``) can only be after a keyword to replace an unspecified number of characters.                              |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | ?                                 | Fuzzy search. The question mark (?) is in the middle or at the end of a keyword to replace a character.                                     |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   Operators (such as **&&**, **\|\|**, **AND**, **NOT**, **\***, **?**, and **:**) contained in raw logs cannot be used to search for logs.

The rules for searching for logs by keyword are as follows:

-  Fuzzy search is supported.

   For example, if you enter **error\***, all logs that contain **error** will be displayed and especially those start with **error** will be highlighted.

-  Search based on combined conditions (including **host_name:**, **ip:**, **path:**, and **time:**) is supported. The format is **key1:value1** *[condition]* **key2:value2**, for example, **host_name:ecs-rxm NOT ip:192.168.1.205 AND path:/home/home.log**.

The following are examples:

-  **query1 AND query2**: logs that contain **query1** and **query2**
-  **query1 OR query2**: logs that contain **query1** or **query2**
-  **query1 NOT query2**: logs that contain **query1** but not **query2**
-  **error\***: logs that contain **error**
-  **er?or**: logs that start with **er**, is followed by any single character, and end with **or**
-  **query1 AND query2 NOT query3**: logs that contain **query1** and **query2** but not **query3**

   .. note::

      -  Characters connected with an underscore (_) will be deemed as a word and cannot be split during log search.
      -  When you enter a keyword to query logs, the keyword is case-insensitive. Log contents you queried are case-insensitive but the highlighted log contents are case-sensitive.
      -  Fuzzy search. The wildcard (*) and question mark (?) cannot be replaced with some special characters such as hyphens (-) and spaces.

Searching for Logs
------------------

To set search filters and a time range, perform the following operations:

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

#. In the log group list on the **Log Management** page, click the name of the target log group.

#. In the log stream list, click the name of the target log stream.

   Alternatively, you can click **Search** in the **Operation** column of the row that contains the target log stream.

#. On the displayed page, enter your keyword in the search box by following the instructions in :ref:`Search Syntax and Examples <lts_01_0013__section118029111411>`.


   .. figure:: /_static/images/en-us_image_0000001904515018.png
      :alt: **Figure 1** Search box

      **Figure 1** Search box

#. Select a time range in the upper right corner.

#. Click the search icon to start the search.

   Logs containing the keyword are displayed.

Configuring Quick Search
------------------------

To search for logs using a keyword repeatedly, perform the following operations to configure a quick search:

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

#. In the log group list on the **Log Management** page, click the name of the target log group.

#. In the log stream list, click the name of the target log stream.

   Alternatively, you can click **Search** in the **Operation** column of the row that contains the target log stream.

#. Set search filters by following the instructions in :ref:`Search Syntax and Examples <lts_01_0013__section118029111411>`.

   For example, you can enter **error\***.

#. Click **Add Quick Search**.


   .. figure:: /_static/images/en-us_image_0000001904361790.png
      :alt: **Figure 2** Adding quick search

      **Figure 2** Adding quick search

#. Enter a quick search name.

   The quick search name must meet the following requirements:

   -  Can contain 1 to 64 characters.
   -  Only allows uppercase and lowercase letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot start or end with a period.
   -  Must be unique in a log stream.

#. Click **OK**.

   Added query search filters are displayed next to **Add Quick Search**. Click the name of a quick search filter to view the search results.

Viewing Context of a Log
------------------------

To facilitate fault location during O&M, perform the following operations to query logs generated within the time range before and after the time when a log is generated:

#. Log in to the management console.
#. In the upper left corner of the management console, select the target region and project.
#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

4. In the log group list on the **Log Management** page, click the target log group.

5. In the log stream list, click the target log stream.

   Alternatively, you can click **Search** in the **Operation** column of the row that contains the target log stream.

6. Set search filters by following the instructions in :ref:`Search Syntax and Examples <lts_01_0013__section118029111411>`.

7. In the search result, click **View Context** on the right of the log to be viewed.

   Details of several logs generated before and after the log are displayed.
