:original_name: lts-07213.html

.. _lts-07213:

Search and Analysis
===================

This section describes the restrictions on LTS query and analysis.

Search
------

.. table:: **Table 1** Log search restrictions

   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Item                                | Description                                                                                                                   | Remarks               |
   +=====================================+===============================================================================================================================+=======================+
   | Delay from log collection to search | Logs can be searched on the console within 2 minutes after being generated (congestion not considered).                       | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Keywords                            | Keywords are conditions excluding Boolean logic operators during query. Up to 30 keywords are supported for a query.          | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Concurrent queries                  | Up to 600 concurrent queries per minute are supported in an account.                                                          | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Returned records                    | Up to 250 records are returned by default for a query on the console.                                                         | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   |                                     | Up to 5000 records are returned by default for an API query.                                                                  | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Field size                          | The maximum size of a field value is 2 KB. The excess part will not be used for quick analysis but can be queried by keyword. | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Search result sorting               | By default, search results are displayed by time (accurate to the second) in descending order.                                | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Fuzzy search                        | -  Each word in a query statement must be fewer than 255 characters.                                                          | N/A                   |
   |                                     |                                                                                                                               |                       |
   |                                     | -  Words cannot start with an asterisk (*) or a question mark (?).                                                            |                       |
   |                                     | -  Long and double data does not support fuzzy search using asterisks (*) or question marks (?).                              |                       |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Time range                          | No longer than 30 days                                                                                                        | N/A                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------------+
