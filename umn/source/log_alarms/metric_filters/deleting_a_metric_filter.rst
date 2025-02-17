:original_name: lts_04_0024.html

.. _lts_04_0024:

Deleting a Metric Filter
========================

Scenario
--------

You can create up to 5 metric filters in each log stream. If you want to create a filter but fail to do so because the upper limit has been reached, delete an unnecessary filter and try again.

Prerequisites
-------------

-  You have obtained an account and its password for logging in to the console.
-  You have created a log group.
-  You have created a log stream.
-  Logs have been collected.
-  You have created a metric filter.

Procedure
---------

#. Log in to the console.

#. Choose |image1| > **Management & Deployment** > **Log Tank Service**.

   Choose **Log Management**.

#. In the log group list, click |image2| of the target log group.

#. In the log stream list, locate the target log stream.

#. Click the number or hyphen in the **Metric Filter Numbers** column.

#. Click **Delete** in the row where the target filter is located.

   .. note::

      After the filter is deleted, the metric corresponding to the filter will stop being monitored by AOM. The previously configured alarm rules may trigger an alarm due to insufficient data.

.. |image1| image:: /_static/images/en-us_image_0000001130122307.png
.. |image2| image:: /_static/images/en-us_image_0000002115137253.png
