:original_name: lts_04_0004.html

.. _lts_04_0004:

Managing Log Streams
====================

A log stream is the basic unit for reading and writing logs. You can put different types of logs into different streams for easier management. For example, you can sort logs (such as operation logs and access logs) into different log streams, making it easier to view specific logs when you query them.

Up to 100 log streams can be created in a log group. The upper limit cannot be increased. If you cannot create a log stream because the upper limit is reached, you are advised to delete log streams that are no longer needed and try again, or create log streams in a new log group.

Prerequisites
-------------

You have created a log group.

Creating a Log Stream
---------------------

#. On the LTS console, click |image1| on the left of a log group name.
#. Click **Create Log Stream** in the upper left corner of the displayed page, and enter a log stream name. After a log stream is created, its name cannot be changed. A log stream name:

   -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  Cannot start with a period (.) or underscore (_) or end with a period (.).
   -  Can contain 1 to 64 characters.

   .. note::

      Collected logs are sent to the created log stream. If there are a large number of logs, you can create multiple log streams and name them for quick log search. After a log stream is created, its name cannot be changed.

#. Click **OK**. In the log stream list, view information such as log stream names and operations.

Deleting a Log Stream
---------------------

You can delete a log stream that is no longer needed. Deleting a log stream will also delete the log data in the log stream. Deleted log streams cannot be recovered. Exercise caution when performing the deletion.

.. note::

   -  Before deleting a log stream, check whether any log collection task is configured for it. If there is a log collection task, deleting the log stream may affect log reporting.
   -  If you want to delete a log stream that is associated with a log transfer task, delete the task first.

#. In the log stream list, locate the target log stream and click |image2| in the **Operation** column.
#. Enter **DELETE** and click **OK**.

Other Operations
----------------

-  Adding a log stream to favorites

   Click |image3| in the **Operation** column of a log stream to add the log stream to favorites. The log stream is then displayed in **My Favorites**/**My Favorites (Local Cache)** on :ref:`the console home page <lts_04_1153__en-us_topic_0000001217194912_section1179111313129>`.

-  Configuring a metric filter

   Click |image4| in the **Operation** column of a log stream. On the displayed page, configure the metric filter.

   .. note::

      LTS extracts your specified keyword from logs so that you can monitor it and set alarms on AOM.

.. |image1| image:: /_static/images/en-us_image_0000001217758588.png
.. |image2| image:: /_static/images/en-us_image_0000001543219709.png
.. |image3| image:: /_static/images/en-us_image_0000001262713829.png
.. |image4| image:: /_static/images/en-us_image_0000001483508528.png
