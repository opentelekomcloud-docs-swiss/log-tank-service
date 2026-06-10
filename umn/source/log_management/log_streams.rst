:original_name: lts_04_0004.html

.. _lts_04_0004:

Log Streams
===========

A log stream is the basic unit for reading and writing logs. You can separate different types of logs (such as operation logs and access logs) into different log streams for easier management. Sorting logs into different log streams makes it easier to find specific logs when you need them.

Up to 100 log streams can be created in a log group. The upper limit cannot be increased. If you cannot create a log stream because the upper limit is reached, you are advised to delete log streams that are no longer needed and try again, or create log streams in a new log group.

Prerequisites
-------------

You have created a log group.

Creating a Log Stream
---------------------

#. On the LTS console, click |image1| on the left of a log group name.
#. Click **Create Log Stream** in the upper left corner of the displayed page, and enter a log stream name. After a log stream is created, its name cannot be changed. A log stream name:

   -  Can contain only letters, digits, underscores (_), hyphens (-), and periods (.). It cannot start with a period or underscore, or end with a period.
   -  Can contain 1 to 64 characters.

   .. note::

      Collected logs are sent to the created log stream. If there are a large number of logs, you can create multiple log streams and name them for quick log search.

#. If you enable **Log Retention Duration** on this page, you can set the log retention duration specifically for the log stream. If you disable it, the log stream will inherit the log retention setting of the log group.
#. Click **Add Tags** and enter a tag key and value. To add more tags, repeat this step. A maximum of 20 tags can be added.
#. Enter remarks. A maximum of 1,024 characters are allowed.
#. Click **OK**.

Modifying a Log Stream
----------------------

By default, a log stream inherits the log retention setting from the log group it belongs to.

#. In the log stream list, locate the target log stream and click |image2| in the **Operation** column.
#. In the dialog box displayed, modify the log stream name and log retention duration.

   .. note::

      -  If you disable **Log Retention Duration**, the log stream will inherit the log retention setting of the log group.
      -  If you enable **Log Retention Duration**, you can set the log retention duration specifically for the log stream.
      -  The logs that exceed the retention period will be deleted automatically. You can transfer logs to OBS buckets for long-term storage.
      -  For details about how to add a tag, see :ref:`Tag Management <lts_04_1217>`.

#. Click **OK**.
#. After the modification is successful, move the cursor over the log stream name. The new and original log stream names are displayed.

Deleting a Log Stream
---------------------

You can delete a log stream that is no longer needed. Deleting a log stream will also delete the log data in the log stream. Deleted log streams cannot be recovered. Exercise caution when performing the deletion.

.. note::

   -  Before deleting a log stream, check whether any log collection task is configured for it. If there is a log collection task, deleting the log stream may affect log reporting.
   -  If you want to delete a log stream that is associated with a log transfer task, delete the task first.

#. In the log stream list, locate the target log stream and click |image3| in the **Operation** column.
#. Enter **DELETE** and click **OK**.

Other Operations
----------------

-  Adding a log stream to favorites

   Click |image4| in the **Operation** column of a log stream to add the log stream to favorites. The log stream is then displayed in **My Favorites**/**My Favorites (Local Cache)** on the :ref:`Log Management <lts_04_1153__en-us_topic_0000001217194912_section1179111313129>` page.

-  Configuring a metric filter

   Click |image5| in the **Operation** column of a log stream. On the displayed page, configure the metric filter.

   .. note::

      LTS extracts your specified keyword from logs, enabling you to monitor log metrics and receive alarms via Application Operations Management (AOM).

-  **Details**

   Click |image6| in the **Operation** column of a log stream to view its details, including the log stream name, log stream ID, and creation time.

.. |image1| image:: /_static/images/en-us_image_0000001217758588.png
.. |image2| image:: /_static/images/en-us_image_0000001559214346.png
.. |image3| image:: /_static/images/en-us_image_0000001543219709.png
.. |image4| image:: /_static/images/en-us_image_0000001262713829.png
.. |image5| image:: /_static/images/en-us_image_0000001483508528.png
.. |image6| image:: /_static/images/en-us_image_0000001565201540.png
