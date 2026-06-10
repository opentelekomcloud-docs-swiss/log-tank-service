:original_name: lts_08301.html

.. _lts_08301:

Creating Log Groups and Log Streams
===================================

Log groups and log streams are basic units for log management in LTS. Before using LTS, create a log group and a log stream.

Prerequisites
-------------

You have obtained an account and its password for logging in to the console.

Creating a Log Group
--------------------

#. Log in to the LTS console. On the **Log Management** page, click **Create Log Group**.
#. On the displayed page, enter a log group name.

   .. note::

      -  Collected logs are sent to the log group. If there are too many logs to collect, separate logs into different log groups based on log types, and name log groups in an easily identifiable way.
      -  A log group name can contain 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). It cannot start with a period or underscore or end with a period.

#. Set **Log Retention Duration** to one to seven days.
#. Click **Add Tags** and enter a tag key and value. If you enable **Apply to Log Stream**, the tag will be applied to all log streams in the log group. To add more tags, repeat this step. A maximum of 20 tags can be added.
#. Enter remarks. A maximum of 1,024 characters are allowed.
#. Click **OK**.

Creating a Log Stream
---------------------

#. Click |image1| on the left of a log group name.
#. Click **Create Log Stream**.
#. In the dialog box displayed, enter a log stream name.

   .. note::

      -  A log stream name can contain 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). It cannot start with a period or underscore or end with a period.
      -  Collected logs are sent to the created log stream. If there are a large number of logs, you can create multiple log streams and name them for quick log search.

#. Enable **Log Retention Duration** as required. If you enable it, you can set the log retention duration specifically for the log stream. If you disable it, the log stream will inherit the log retention setting of the log group.
#. Click **Add Tags** and enter a tag key and value. To add more tags, repeat this step. A maximum of 20 tags can be added.
#. Enter remarks. The value contains up to 1,024 characters.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001637679773.png
