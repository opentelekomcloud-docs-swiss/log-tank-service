:original_name: lts_05_0007.html

.. _lts_05_0007:

Quick Analysis
==============

Monitoring keywords in logs helps you keep track of system performance and services. For example, the number of **ERROR** keywords indicates the system health, and the number of **BUY** keywords indicates the sales volume. LTS provides quick analysis for you to obtain statistics on your specified keywords.

Prerequisites
-------------

Quick analysis is conducted on fields extracted from structured logs. :ref:`Structure <lts_0821>` raw logs before you create a quick analysis task.

Creating a Quick Analysis Task
------------------------------

You can enable **Quick Analysis** for the fields on the **Log Structuring** page. You can also perform the following steps to create a quick analysis task:

#. Log in to the LTS console. In the navigation pane on the left, choose **Log Management**.
#. A quick analysis is performed on a log stream. Select the target log group and log stream on the **Log Management** page.
#. On the **Raw Logs** tab page, click **Set Quick Analysis**. On the displayed page, add the fields that require quick analysis.
#. Click **OK**. The quick analysis task is created.

   .. note::

      -  |image1| indicates a field of the **string** type.
      -  |image2| indicates a field of the **float** type.
      -  |image3| indicates a field of the **long** type.
      -  The maximum length of a field for quick analysis is 2000 bytes.
      -  The quick analysis field area displays the first 100 records.

.. |image1| image:: /_static/images/en-us_image_0000001588482889.png
.. |image2| image:: /_static/images/en-us_image_0000001298698089.png
.. |image3| image:: /_static/images/en-us_image_0000001252258790.png
