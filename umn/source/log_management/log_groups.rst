:original_name: lts_04_0003.html

.. _lts_04_0003:

Log Groups
==========

A log group is a group of log streams. Up to 100 log groups can be created for a single account.

Prerequisites
-------------

You have obtained an account and its password for logging in to the LTS console.

Creating a Log Group
--------------------

#. Log in to the LTS console. On the **Log Management** page, click **Create Log Group**.
#. In the dialog box displayed, enter a log group name.

   .. note::

      -  Collected logs are sent to the log group. If there are too many logs to collect, separate logs into different log groups based on log types, and name log groups in an easily identifiable way.
      -  A log group name can contain 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). It cannot start with a period or underscore or end with a period.

#. Set **Log Retention Duration** to one to seven days.
#. Click **Add Tags** and enter a tag key and value. If you enable **Apply to Log Stream**, the tag will be applied to all log streams in the log group. To add more tags, repeat this step. A maximum of 20 tags can be added.
#. Enter remarks. A maximum of 1,024 characters are allowed.
#. Click **OK**.

Modifying a Log Group
---------------------

You can modify the log name, log retention duration, or remarks of a log group by performing the following steps:

#. In the log group list, locate the target log group and click **Modify** in the **Operation** column.
#. Modify the log name and log retention duration on the displayed page.
#. Click **OK**.
#. After the modification is successful, move the cursor over the log group name. The new and original log group names are displayed.

Deleting a Log Group
--------------------

You can delete a log group that is no longer needed. Deleting a log group will also delete the log streams and log data in the log group. Deleted log groups cannot be recovered. Exercise caution when performing the deletion.

.. note::

   If you want to delete a log group that is associated with a log transfer task, delete the task first.

#. In the log group list on the **Log Management** page, locate the target log group and click **Delete** in the **Operation** column.
#. Enter **DELETE** and click **OK**.

Searching Log Groups/Streams
----------------------------

In the log group list, click the search box and set the following filter criteria:

-  Log group/stream
-  Original log group/stream name
-  Log group name/ID
-  Log stream name/ID
-  Log group tag
-  Remarks

Other Operations
----------------

To view the details of a log group, go to the log group list and click **Details** in the **Operation** column of the desired log group, including the log group name, ID, and creation time.
