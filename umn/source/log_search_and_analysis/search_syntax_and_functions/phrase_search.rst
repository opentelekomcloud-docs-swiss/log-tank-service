:original_name: lts_05_0112.html

.. _lts_05_0112:

Phrase Search
=============

Phrase search is used to precisely match the target phrase. For example, the search statement **abc def** matches all logs that contain both **abc** and **def** regardless of the sequence. For details about the differences between phrase search and keyword search, see :ref:`Table 1 <lts_05_0112__en-us_topic_0000001564118726_table1863692594020>`.

-  Phrase search: It is built on keyword search syntax but adds positional awareness. It ensures that keywords appear in the exact sequence specified, allowing for high-precision matching of specific phrases. Phrase search is applicable to English phrases. It cannot be used together with fuzzy search.

-  Keyword search: It is based on word segmentation. The system uses delimiters to split the search content into individual tokens to find matching logs. Keyword search does not distinguish the sequence of words. A log is returned as long as the keywords satisfy the specified Boolean logic (**AND**, **OR**, or **NOT**), regardless of their order.

   .. _lts_05_0112__en-us_topic_0000001564118726_table1863692594020:

   .. table:: **Table 1** Differences between two search modes

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
      | Search Mode           | Phrase Search                                                                                                                  | Keyword Search                                                                                   |
      +=======================+================================================================================================================================+==================================================================================================+
      | Differences           | Distinguishes the sequence of keywords and is used to accurately match target phrases, making the search result more accurate. | Does not distinguish the sequence of keywords. The keyword is matched based on the search logic. |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
      | Examples              | Assume that your log stream contains the following two raw logs:                                                               |                                                                                                  |
      |                       |                                                                                                                                |                                                                                                  |
      |                       | -  Raw log 1: **this service is lts**                                                                                          |                                                                                                  |
      |                       | -  Raw log 2: **lts is service**                                                                                               |                                                                                                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
      |                       | If you search for the phrase **#"is lts"**, one log is matched.                                                                | If you search for the keyword **is lts**, two logs are matched.                                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
      |                       | If you search for the phrase **#"lts is"**, one log is matched.                                                                | If you search for the keyword **lts is**, two logs are matched.                                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

Search Syntax
-------------

.. table:: **Table 2** Search Mode

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Search Mode                       | Description                                                                                                                                                                        |
   +===================================+====================================================================================================================================================================================+
   | Full-text search                  | -  #"abc def"                                                                                                                                                                      |
   |                                   | -  content:#"abc def"                                                                                                                                                              |
   |                                   |                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                    |
   |                                   |    **content** is a built-in field corresponding to the original log text. **#"abc def"** is equivalent to **content:#"abc def"** and matches the original log content by default. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Field Search                      | key:#"abc def"                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                    |
   |                                   | .. note::                                                                                                                                                                          |
   |                                   |                                                                                                                                                                                    |
   |                                   |    -  The value cannot be empty.                                                                                                                                                   |
   |                                   |    -  When field search is used together with the not operator, logs that do not contain this field are matched.                                                                   |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Constraints
-----------

-  Fuzzy search cannot be used together with phrase search.

   The asterisk (``*``) and question mark (?) in phrase search are regarded as common characters. Therefore, phrase search does not support fuzzy search and can be used to search for the asterisk (``*``) and question mark (?) in logs.

-  Phrase search does not support search by delimiter.

   For example, in the search statement **#"var/log"**, **/** is a delimiter. The search statement is equivalent to **#"var log"**, and is used to search for logs containing the target phrase **var log**. Similarly, search statements such as **#"var:log"** and **#"var;log"** are used to search for logs that contain the target phrase **var log**.

Example
-------

|image1|

.. table:: **Table 3** Search description

   +-----------------------------------------------------------------------------+--------------------------------+
   | Search Requirement                                                          | Search Statement               |
   +=============================================================================+================================+
   | Logs in which the value of User-Agent contains the phrase Mon, 17 Apr 2023. | User-Agent:#"Mon, 17 Apr 2023" |
   +-----------------------------------------------------------------------------+--------------------------------+
   | Logs in which the value of User-Agent contains the phrase Mozilla/5.0.      | User-Agent:#"Mozilla/5.0"      |
   +-----------------------------------------------------------------------------+--------------------------------+
   | Logs in which the value of week contains the phrase Monday.                 | week:#"Monday"                 |
   +-----------------------------------------------------------------------------+--------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001630789585.png
