:original_name: lts_04_0022.html

.. _lts_04_0022:

Creating a Metric Filter
========================

This section describes how you can create a metric filter. The metric will be monitored in AOM. If you set an alarm for the metric, you will be alerted when the number of occurrences of the metric reaches the configured threshold. Up to 5 metric filters can be created in each log stream.

#. Log in to the console.

#. Choose |image1| > **Management & Deployment** > **Log Tank Service**.

   Choose **Log Management**.

#. In the log group list, click |image2| of the target log group.

#. In the log stream list, click |image3| in the **Operation** column of the target log stream.

#. Configure metric filter parameters by referring to :ref:`Table 1 <lts_04_0022__en-us_topic_0293496376_en-us_topic_0187475499_table1177128018503>` and click **OK**.

.. _lts_04_0022__en-us_topic_0293496376_en-us_topic_0187475499_table1177128018503:

.. table:: **Table 1** Metric filter parameters

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   +===================================+===========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Filter Name                       | Filter names are used to distinguish different filters in a log stream. A name cannot start with a period (.) or underscore (_) or end with a period. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed.                                                                                                                                                                                                                                                                    |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Filtering Keyword                 | A filter counts the number of occurrences for the specified keyword in the log stream.                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                                   | Only filtering with a single keyword, such as **Error** and **Warning**, is supported. If you enter multiple keywords, such as **Fail to root**, they are considered as a whole. Filtering is case-sensitive and looks for exact matches. Numbers and special characters must be enclosed by double quotation marks.                                                                                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Sample Log Event                  | Sample log events are used to test whether the filtering can match logs based on the configured keyword. You can click **Select Log Event** to go to the **Raw Logs** tab to search for logs containing the configured keyword and paste them to the test box to check whether the filtering works. You can also modify the keyword.                                                                                                                                                                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Metric Name                       | A metric name maps to a filtering keyword and resembles a key in a key-value pair. LTS carries out metric statistics and releases the results to AOM so you can monitor the frequency of the keyword, set thresholds, and receive alarms when the frequency exceeds the threshold. A metric name can contain 1 to 64 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed. Metric names in a same log stream must be unique. Otherwise, data may be inaccurate. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001083204950.png
.. |image2| image:: /_static/images/en-us_image_0000002115050969.png
.. |image3| image:: /_static/images/en-us_image_0000002144900630.png
