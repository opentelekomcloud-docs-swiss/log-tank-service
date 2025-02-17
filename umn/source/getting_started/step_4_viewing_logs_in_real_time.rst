:original_name: lts_08303.html

.. _lts_08303:

Step 4: Viewing Logs in Real Time
=================================

After the log ingestion is configured, you can view the reported logs on the LTS console in real time.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed ICAgent.
-  You have ingested logs.

Viewing Logs in Real Time
-------------------------

#. Log in to the LTS console and choose **Log Management**.

#. In the log group list, click the name of a log group.

#. In the log stream list, click the name of a log stream.

#. On the log stream details page, click **Real-Time Logs** to view logs in real time.

   Logs are reported to LTS once every five seconds. You may wait for at most five seconds before the logs are displayed.

   You can control log display by clicking **Clear** or **Pause** in the upper right corner.

   -  **Clear**: Displayed logs will be cleared from the real-time view.

   -  **Pause**: Loading of new logs to the real-time view will be paused.

      After you click **Pause**, the button changes to **Continue**. You can click **Continue** to resume the log loading to the real-time view.

      .. note::

         Stay on the **Real-Time Logs** tab to keep updating them in real time. If you leave the **Real-Time Logs** tab, logs will stop being loaded in real time.
