:original_name: lts_01_0026.html

.. _lts_01_0026:

Deleting a Log Transfer Task
============================

Scenarios
---------

This section describes how to delete a log transfer task.

.. note::

   -  Deleting log transfer tasks will stop transferring any logs. Therefore, exercise caution when performing this deletion operation.
   -  After a log transfer task is deleted, the logs that have been transferred to your Object Storage Service (OBS) bucket will be continually stored.

Prerequisites
-------------

-  You have created a log group.
-  You have created a log stream.
-  You have configured a log transfer task.

Procedure
---------

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

#. In the navigation pane on the left, choose **Log Transfer**.

#. In the log group list, locate the target log group and click **Delete** in the **Operation** column.

   The **Delete Log Transfer** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001904377816.png
      :alt: **Figure 1** Deleting a log transfer task

      **Figure 1** Deleting a log transfer task

#. Click **Yes**.
