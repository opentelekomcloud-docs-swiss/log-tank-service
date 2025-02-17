:original_name: lts_08301.html

.. _lts_08301:

Step 1: Creating Log Groups and Log Streams
===========================================

Log groups and log streams are basic units for log management in LTS. Before using LTS, create a log group and a log stream.

Prerequisites
-------------

You have obtained an account and its password for logging in to the console.

Creating a Log Group
--------------------

#. Log in to the LTS console. On the **Log Management** page, click **Create Log Group**.

#. In the dialog box displayed, enter a log group name.

   .. note::

      Collected logs are sent to the log streams of the corresponding log groups. If there are a large number of logs, name log groups and log streams in an easily identifiable way so that you can quickly find the logs you desire.

      A log group name:

      -  Can contain only letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot start with a period or underscore, or end with a period.
      -  Can contain 1 to 64 characters.

#. Set **Log Retention Duration**. Logs are retained for seven days by default.

#. Click **OK**.

Creating a Log Stream
---------------------

#. Click |image1| on the left of a log group name and click **Create Log Stream**.
#. In the dialog box displayed, enter a log stream name.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002180001757.png
