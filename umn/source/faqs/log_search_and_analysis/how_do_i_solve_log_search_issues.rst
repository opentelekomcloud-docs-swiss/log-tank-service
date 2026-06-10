:original_name: lts_faq_0140.html

.. _lts_faq_0140:

How Do I Solve Log Search Issues?
=================================

This topic describes how to troubleshoot common issues that occur when the search syntax is used to query logs.

Common Issues and Troubleshooting Methods
-----------------------------------------

#. During log query, a message is displayed indicating that the query result is inaccurate.

   -  Possible cause: There are too many logs in the query time range, and not all logs are displayed.
   -  Solution: Click the query button multiple times until you obtain all logs, or shorten the query time range and query again.

#. Too many log results are matched in a query.

   -  Possible cause: Only phrase search **#"value"** can ensure the sequence of keywords. For example, if the query statement is **abc def**, logs that contain either **abc** or **def** and logs that contain the phrase **abc def** will be matched.
   -  Solution: Use the phrase **#"abc def"** to accurately match logs containing the phrase **abc def**.

#. Expected logs cannot be queried with specific search statements, and no error message is displayed.

   -  Possible cause 1: Search delimiters are not supported.
   -  Possible cause 2: The **\*** or **?** in a search statement will be regarded as a common character and is not used as a wildcard.
   -  Solution: Use the correct query statement.

Error Messages and Solutions
----------------------------

#. An error message is displayed during log query, indicating that no field index is configured for the XXX field and the field cannot be queried.

   Solution: Create an index for the *XXX* field in the index configuration and run the query statement again.

#. An error message is displayed during log query, indicating that the full-text index is not enabled and the content field and full-text query are not supported.

   Solution: Enable whole text indexing in the index configuration and run the query statement again.

#. An error message is displayed during log query, indicating that the asterisk (*) or question mark (?) cannot be used at the beginning of a word.

   Solution: Modify the query statement or use a correct delimiter to avoid such queries.

#. An error message is displayed during log query, indicating that long and float fields do not support fuzzy query using asterisks (*) or question marks (?).

   Solution: Modify the query statement and use the operator (>=<) or IN syntax for range query.

#. An error message is displayed during log query, indicating that string fields do not support range query using the operator (>=<) or IN syntax.

   Solution

   -  Modify the query statement and use the asterisk (*) or question mark (?) to perform fuzzy query.
   -  Change the value of this field to a number.

#. An error message is displayed during log query, indicating that the search syntax is incorrect and the query statement need to be modified.

   -  Possible cause: The syntax of the operator is incorrect.

      Solution: Each operator has its syntax rule. Modify the search statement. For details, see Search Syntax. For example, the syntax rule for the operator = requires that the value on the right must be digits.

   -  Possible cause: The search statement contains syntax keywords.

      Solution: If the log to search contains syntax keywords, the search statement must be enclosed in double quotation marks to convert the keywords into common characters. For example, if **and** is a syntax keyword, change the query statement **field:and** to **field:"and"**.
