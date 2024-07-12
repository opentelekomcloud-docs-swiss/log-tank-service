:original_name: lts_01_0024.html

.. _lts_01_0024:

Viewing a Log Transfer Task
===========================

Scenarios
---------

This section describes how to view a log transfer task.

The status of a transfer task can be **Normal**, **Abnormal**, or **Disabled** as follows:

-  **Normal**: indicates that the log transfer task works properly.
-  **Abnormal**: indicates that the OBS bucket to which logs are transferred is deleted or the bucket policy is abnormal. Rectify the fault by following the instructions in :ref:`Why Is Log Transfer Abnormal on the Log Transfer Page? <lts_01_0030>`
-  **Disabled**: indicates that the log transfer task is stopped.

You can enable or disable a log transfer task by following the instructions in :ref:`Modifying a Log Transfer Task <lts_01_0025>`.

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

#. In the log transfer task list, view the target log transfer task.


   .. figure:: /_static/images/en-us_image_0224007647.png
      :alt: **Figure 1** Viewing log transfer tasks

      **Figure 1** Viewing log transfer tasks
