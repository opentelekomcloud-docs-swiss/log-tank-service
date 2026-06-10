:original_name: lts_0825.html

.. _lts_0825:

Log Structuring Fields
======================

Constraints
-----------

The maximum size of a structured field value is 16 KB. The excess part will be truncated.

.. _lts_0825__en-us_topic_0000001481908120_section13954165812210:

Setting Log Structuring Fields
------------------------------

You can edit extracted fields after log structuring.

.. table:: **Table 1** Rules for configuring structured fields

   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+
   | Structuring Method                   | Field Name                                                                                                                   | Field Type Can Be Changed | Field Can Be Deleted |
   +======================================+==============================================================================================================================+===========================+======================+
   | Regular expressions (auto generate)  | User-defined.                                                                                                                | Yes                       | Yes                  |
   |                                      |                                                                                                                              |                           |                      |
   |                                      | The name must start with a letter and contain only letters and digits.                                                       |                           |                      |
   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+
   | Regular expressions (manually enter) | -  User-defined.                                                                                                             | Yes                       | Yes                  |
   |                                      | -  Default names such as **field1**, **field2**, and **field3** will be used for unnamed fields. You can modify these names. |                           |                      |
   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+
   | JSON                                 | Names are set automatically, but you can set aliases for fields.                                                             | Yes                       | Yes                  |
   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+
   | Delimiter                            | Default names such as **field1**, **field2**, **field3** are used. You can modify these names.                               | Yes                       | Yes                  |
   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+
   | Nginx                                | Names are set based on Nginx configuration, but you can set aliases for fields.                                              | Yes                       | Yes                  |
   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+
   | Custom templates                     | User-defined.                                                                                                                | Yes                       | Yes                  |
   +--------------------------------------+------------------------------------------------------------------------------------------------------------------------------+---------------------------+----------------------+

.. note::

   When you use regular expressions (manually entered), JSON, delimiters, Nginx, or custom templates to structure logs, field names:

   -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).
   -  Cannot start with a period (.) or underscore (_) or end with a period (.).
   -  Can contain 1 to 64 characters.

Setting Tag Fields
------------------

When configuring log structuring, you can set the tag fields for the log information.

#. During field extraction, click the **Tag Fields** tab.
#. Click **Add Field**.
#. In the **Field** column, enter the name of the tag field, for example, **hostIP**.

   .. note::

      If you configure tag fields for a structuring rule that was created before the function of tag fields was brought online, no example values will be shown with the tag fields.

#. To add more fields, click **Add Field**.
#. Click **Save** to save the settings.

   .. note::

      -  Tag fields can be the following system fields: **category**, **clusterId**, **clusterName**, **containerName**, **hostIP**, **hostId**, **hostName**, **nameSpace**, **pathFile**, and **podName**.
      -  Tag fields cannot be the following system fields: **groupName**, **logStream**, **lineNum**, **content**, **logContent**, **logContentSize**, and **collectTime**.
      -  You can configure both field extraction and tag fields during log structuring.
