:original_name: lts_0823.html

.. _lts_0823:

Structuring Modes
=================

LTS provides five log structuring modes: regular expressions, JSON, delimiter, Nginx, and structuring template. You can make your choice flexibly.

.. _lts_0823__en-us_topic_0000001532627437_section1193293314459:

Regular Expressions
-------------------

If you choose regular expressions, fields are extracted based on your defined regular expressions.

#. Select a typical log event as the sample.

   -  Click **Select from existing log events**, select a log event, and click **OK**. You can select different time ranges to filter logs.
   -  Click **Paste from Clipboard** to copy the cut log content to the sample log box.

      .. note::

         There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

         -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
         -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
         -  **Specified**: queries log data that is generated in a specified time range.

2. Extract fields. Extracted fields are shown with their example values. You can extract fields in two ways:

   -  **Auto generate**: Select the log content you want to extract as a field in the sample log event. In the dialog box displayed, set the field name. The name must start with a letter and contain only letters and digits. Then click Add.
   -  **Manually enter**: Enter a regular expression in the text box and click **Extract Field**. A regular expression may contain multiple capturing groups, which group strings with parentheses. There are three types of capturing groups:

      -  (*exp*): Capturing groups are numbered by counting their opening parentheses from left to right. The numbering starts with 1.
      -  (?<*name*>\ *exp*): named capturing group. It captures text that matches *exp* into the group *name*. The group name must start with a letter and contain only letters and digits. A group is recalled by group name or number.
      -  (?:*exp*): non-capturing group. It captures text that matches *exp*, but it is not named or numbered and cannot be recalled.

   .. note::

      -  When you select **manually enter**, the regular expression can contain up to 5000 characters. You do not have to name capturing groups when writing the regular expression. When you click **Extract Field**, those unnamed groups will be named as **field1**, **field2**, **field3**, and so on.

3. Click **Save**. The type of extracted fields cannot be changed after the structuring is complete.

.. _lts_0823__en-us_topic_0000001532627437_section11217131014476:

JSON
----

If you choose **JSON**, JSON logs are split into key-value pairs.

#. Select a typical log event as the sample. Click **Select from existing log events**, select a log event, or enter a log event in the text box, and click **OK**. You can select different time ranges to filter logs.

   .. note::

      There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

      -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  **Specified**: queries log data that is generated in a specified time range.

2. Extract fields. Extract fields from the log event. Extracted fields are shown with their example values.

   Click **Intelligent Extraction**. Take the following log event as an example.

   Enter the log event in the text box.

   .. code-block::

      {"a1": "a1", "b1": "b1", "c1": "c1", "d1": "d1"}

   .. note::

      -  The **float** data type has 16 digit precision. If a value contains more than 16 valid digits, the extracted content is incorrect, which affects visualization and quick analysis. In this case, you are advised to change the field type to **string**.
      -  If the data type of the extracted fields is set to **long** and the log content contains more than 16 valid digits, only the first 16 valid digits are displayed, and the subsequent digits are changed to 0.
      -  If the data type of the extracted fields is set to **long** and the log content contains more than 21 valid digits, the fields are identified as the **float** type. You are advised to change the field type to **string**.

   Check and edit the fields if needed. For details about rules for configuring extracted fields, see :ref:`Setting Log Structuring Fields <lts_0825__en-us_topic_0000001481908120_section13954165812210>`.

3. Click **Save**. The type of extracted fields cannot be changed after the structuring is complete.

.. _lts_0823__en-us_topic_0000001532627437_section1626915495415:

Delimiter
---------

Logs can be parsed by delimiters, such as commas (,), spaces, or other special characters.

#. Select a typical log event as the sample. Click **Select from existing log events**, select a log event, or enter a log event in the text box, and click **OK**. You can select different time ranges to filter logs.

   .. note::

      There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

      -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  **Specified**: queries log data that is generated in a specified time range.

#. Select or customize a delimiter.

   .. note::

      -  For invisible characters, enter hexadecimal characters starting with 0x. The length ranges from 0 to 4 characters. There are 32 invisible characters in total.
      -  For custom characters, enter 1 to 10 characters, each as an independent delimiter.
      -  For custom character string, enter 1 to 30 characters as one whole delimiter.

3. Extract fields. Extract fields from the log event. Extracted fields are shown with their example values.

   Click **Intelligent Extraction**. Take the following log event as an example.

   Enter the log event in the text box.

   .. code-block::

      1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd 192.168.0.154 192.168.3.25 38929 53 17 1 96 1548752136 1548752736 ACCEPT OK

   .. note::

      The **float** data type has seven digit precision.

      If a value contains more than seven valid digits, the extracted content is incorrect, which affects visualization and quick analysis. In this case, you are advised to change the field type to **string**.

   Check and edit the fields if needed. For details about rules for configuring extracted fields, see :ref:`Setting Log Structuring Fields <lts_0825__en-us_topic_0000001481908120_section13954165812210>`.

4. Click **Save**. The type of extracted fields cannot be changed after the structuring is complete.

.. _lts_0823__en-us_topic_0000001532627437_section1710931975616:

Nginx
-----

You can customize the format of access logs by the **log_format** command.

#. Select a typical log event as the sample. Click **Select from existing log events**, select a log event, or enter a log event in the text box, and click **OK**. You can select different time ranges to filter logs.

   .. note::

      There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

      -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  **Specified**: queries log data that is generated in a specified time range.

#. Define the Nginx log format. You can click **Apply Default Nginx Log Format** to apply the default format,

   .. note::

      In standard Nginx configuration files, the portion starting with **log_format** indicates the log configuration.

      Log format

      -  Default Nginx log format:

         .. code-block::

            log_format  main   '$remote_addr - $remote_user [$time_local] "$request" '
                                        '$status $body_bytes_sent "$http_referer" '
                                        '"$http_user_agent" "$http_x_forwarded_for"';

      -  You can also customize a format. The format must meet the following requirements:

         -  Cannot be blank.
         -  Must start with **log_format** and contain apostrophes (') and field names.
         -  Can contain up to 5000 characters.
         -  Must match the sample log event.
         -  Any character except letters, digits, underscores (_), and hyphens (-) can be used to separate fields.
         -  Must end with an apostrophe (') or an apostrophe plus a semicolon (";).

3. Extract fields. Extract fields from the log event. Extracted fields are shown with their example values.

   Click **Intelligent Extraction**. Take the following log event as an example.

   Enter the log event in the text box.

   .. code-block::

      39.149.31.187 - - [12/Mar/2020:12:24:02 +0800] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Safari/537.36" "-"

   Configure the following Nginx log format in step 2:

   .. code-block::

      log_format  main   '$remote_addr - $remote_user [$time_local] "$request" '
                                  '$status $body_bytes_sent "$http_referer" '
                                  '"$http_user_agent" "$http_x_forwarded_for"';

   .. note::

      -  The **float** data type has seven digit precision.
      -  If a value contains more than seven valid digits, the extracted content is incorrect, which affects visualization and quick analysis. In this case, you are advised to change the field type to **string**.

   Check and edit the fields if needed. For details about rules for configuring extracted fields, see :ref:`Setting Log Structuring Fields <lts_0825__en-us_topic_0000001481908120_section13954165812210>`.

4. Click **Save**. The type of extracted fields cannot be changed after the structuring is complete.

.. _lts_0823__en-us_topic_0000001532627437_section81501427185813:

Structuring Template
--------------------

A structuring template extracts fields from either a customized template or a built-in template.

For details, see :ref:`Structuring Templates <lts_0824>`.
