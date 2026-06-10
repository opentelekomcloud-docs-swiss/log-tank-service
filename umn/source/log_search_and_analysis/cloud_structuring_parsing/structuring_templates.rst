:original_name: lts_0824.html

.. _lts_0824:

Structuring Templates
=====================

LTS supports two types of structuring templates: system templates and custom templates.

System Templates
----------------

You can choose from multiple system templates, but cannot modify the field types in them or delete the fields. For details, see :ref:`Table 1 <lts_0824__en-us_topic_0000001532747921_table1181293435214>`.

#. Click **System template** and select a template. A sample log event is displayed for each template.

2. When you select a template, the log parsing result is displayed in the **Template Details** area. Click **Save**.

   .. note::

      -  During log structuring, if a system template is used, the time in the system template is the customized log time.
      -  Fields of the string type do not support range query using the >, =, or < operators or the "in" syntax. Use asterisks (*) or question marks (?) for fuzzy query. You need to reconfigure the structuring and change the value of this field to a number.

   .. _lts_0824__en-us_topic_0000001532747921_table1181293435214:

   .. table:: **Table 1** System template fields

      +--------------------------+--------------------+---------------------------+----------------------+
      | Structuring Method       | Field Name         | Field Type Can Be Changed | Field Can Be Deleted |
      +==========================+====================+===========================+======================+
      | ELB structuring template | Defined by ELB.    | No                        | No                   |
      +--------------------------+--------------------+---------------------------+----------------------+
      | VPC structuring template | Defined by VPC.    | No                        | No                   |
      +--------------------------+--------------------+---------------------------+----------------------+
      | DCS audit logs           | Defined by DCS.    | No                        | No                   |
      +--------------------------+--------------------+---------------------------+----------------------+
      | Tomcat                   | Defined by Tomcat. | No                        | No                   |
      +--------------------------+--------------------+---------------------------+----------------------+
      | Nginx                    | Defined by Nginx.  | No                        | No                   |
      +--------------------------+--------------------+---------------------------+----------------------+

Custom Templates
----------------

Click **Custom template** and select a template. There are two ways to obtain a custom template:

-  When you extract fields using methods of regular expression, JSON, delimiter, or Nginx, click **Save as Template** in the lower left corner. In the displayed dialog box, enter the template name and click **OK**. The template will be displayed in the custom template list.

-  Create a custom template under the **Structuring Template** option.

   Select **Custom template** and click **Create Template**. Enter a template name, select **Regular Expressions**, **JSON**, **Delimiter**, or **Nginx**, configure the template, and click **Save**. The template will be displayed in the custom template list.
