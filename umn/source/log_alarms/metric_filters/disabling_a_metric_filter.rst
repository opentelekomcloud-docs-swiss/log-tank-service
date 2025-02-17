:original_name: lts_04_0023.html

.. _lts_04_0023:

Disabling a Metric Filter
=========================

Scenario
--------

If a filter is no longer needed or becomes invalid because the format or content of logs have changed, you can disable the filter.

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

#. Locate the row where the target filter is located and click **Disable**.

   .. note::

      After the filter is disabled, the metric corresponding to the filter will stop being monitored by AOM.

.. |image1| image:: /_static/images/en-us_image_0000001083524532.png
.. |image2| image:: /_static/images/en-us_image_0000002115051773.png
