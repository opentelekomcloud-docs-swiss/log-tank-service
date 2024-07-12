:original_name: lts_01_0021.html

.. _lts_01_0021:

Deleting a Log Stream
=====================

Scenarios
---------

This section describes how to delete a log stream that will no longer be used.

.. note::

   Ensure that the target log stream is not associated with any log transfer tasks. Deleted log streams cannot be recovered. Exercise caution when performing the deletion.

Prerequisites
-------------

-  You have obtained a username and password for logging in to the management console.
-  You have deleted all log transfer tasks associated with the target log stream.

Procedure
---------

#. Log in to the management console.
#. In the upper left corner of the management console, select the target region and project.
#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

4. In the log group list on the **Log Management** page, click the name of the target log group.

5. In the log stream list, locate the target log stream and click **Delete** in the **Operation** column.

6. Enter **DELETE** and click **Yes**.


   .. figure:: /_static/images/en-us_image_0000001904353322.png
      :alt: **Figure 1** Deleting a log stream

      **Figure 1** Deleting a log stream
