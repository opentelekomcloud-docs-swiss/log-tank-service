:original_name: lts_0822.html

.. _lts_0822:

Overview
========

Log data can be structured or unstructured. Structured data is quantitative data or can be defined by unified data models. It has a fixed length and format. Unstructured data has no pre-defined data models and cannot be fit into two-dimensional tables of databases.

During log structuring, logs with fixed or similar formats are extracted from a log stream based on your defined structuring method and irrelevant logs are filtered out.

Precautions
-----------

-  You have created a log stream.
-  Log structuring is recommended when most logs in a log stream share a similar pattern.
-  After the structuring configuration is modified, the modification takes effect only for newly written log data.

Creating a Structuring Rule
---------------------------

Add structuring rules to a log stream and LTS will extract logs based on the rules.

To structure logs:

#. Log in to the LTS console and choose **Log Management** in the navigation pane.
#. Select a log group and a log stream.
#. On the log stream details page, click |image1| in the upper right corner. On displayed page, switch to the **Cloud Structuring Parsing** tab, and select a structuring method to structure logs.

   -  :ref:`Regular Expression <lts_0823__en-us_topic_0000001532627437_section1193293314459>`
   -  :ref:`JSON <lts_0823__en-us_topic_0000001532627437_section11217131014476>`
   -  :ref:`Delimiter <lts_0823__en-us_topic_0000001532627437_section1626915495415>`
   -  :ref:`Nginx <lts_0823__en-us_topic_0000001532627437_section1710931975616>`
   -  :ref:`Structuring Template <lts_0823__en-us_topic_0000001532627437_section81501427185813>`

   .. note::

      -  If a structured field exceeds 20 KB, only the first 20 KB is retained.
      -  The following system fields cannot be extracted during log structuring: **groupName**, **logStream**, **lineNum**, **content**, **logContent**, **logContentSize**, **collectTime**, **category**, **clusterId**, **clusterName**, **containerName**, **hostIP**, **hostId**, **hostName**, **nameSpace**, **pathFile**, and **podName**.

#. Click **Save**.

Modifying a Structuring Rule
----------------------------

To modify a structuring rule, perform the following steps:

#. On the **Log Structuring** page, click |image2| to modify a structuring rule.

   .. note::

      -  You can modify the structuring rules, including the structuring mode, log extraction field, and tag field.
      -  System templates cannot be modified.

#. Click **Save**.

Deleting a Structuring Rule
---------------------------

If a log structuring rule is no longer used, perform the following steps to delete it:

#. On the **Log Structuring** page, click |image3| to delete a structuring rule.
#. In the displayed dialog box, click **OK**.

   .. note::

      Deleted structuring rules cannot be restored. Exercise caution when performing this operation.

.. |image1| image:: /_static/images/en-us_image_0000001534228257.png
.. |image2| image:: /_static/images/en-us_image_0000001483187872.png
.. |image3| image:: /_static/images/en-us_image_0000001534227573.png
