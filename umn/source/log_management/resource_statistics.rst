:original_name: lts_04_1154.html

.. _lts_04_1154:

Resource Statistics
===================

Log resource statistics are classified into read/write traffic, index traffic, log volume, and raw log traffic. The statistics are for reference only. You can also visualize log resource statistics in charts.

-  **Read/Write**: LTS charges for the amount of compressed log data read from and written to LTS. Generally, the log compression ratio is 5:1.
-  **Indexing**: Raw logs are full-text indexed by default for log search.
-  **Log**: Space used for storing compressed logs, indexes, and copies is billed. The space is roughly the size of the raw logs.
-  **Raw log traffic**: size of raw logs


Resource Statistics
-------------------

Resource statistics display log resource data. By default, log resource data of one week (from now) is displayed. You can select a time range as required.

There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

.. note::

   -  **From now**: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
   -  **From last**: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
   -  **Specified**: queries log data that is generated in a specified time range.

-  The read and write traffic and index traffic data in the selected time range is displayed.
-  Day-on-day changes in the selected time range are displayed. You can view the trend.
-  The traffic trend chart for the selected time range is displayed. Each point in the trend chart indicates the data statistics in a certain period. The unit is KB, MB, or GB. The statistics are collected based on site requirements.

Resource Statistics Details
---------------------------

Resource statistics details display the top 100 log groups or log streams by read/write traffic, index traffic, and latest log volume. By default, the log groups or log streams are sorted by the latest log volume (GB). You can also sort the statistics by read/write or index traffic.

-  For a new log group or log stream, resource statistics will be collected in at least one hour.

-  Click the name of one of the top 100 log groups to query its log stream resource statistics.

-  Click |image1| to download the resource statistics of the target log groups and log streams.

   .. note::

      The downloaded resource statistics of the target log groups and log streams files are in **.CSV** format.

-  You can select a time range to collect statistics on resource details.

   There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

   .. note::

      -  **From now**: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  **From last**: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and **1 hour** is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  **Specified**: queries log data that is generated in a specified time range.

-  The daily log volume (GB), daily index traffic (GB), and daily read/write traffic (GB) are displayed based on the selected time range.

   There are two display modes:

   -  Table
   -  Bar chart

.. |image1| image:: /_static/images/en-us_image_0000001380340913.png
