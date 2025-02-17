:original_name: lts_04_1217.html

.. _lts_04_1217:

Tag Management
==============

You can tag log groups, log streams, host groups, and log ingestion configurations. There are system and custom tags. System tags (such as log cleaning tags) cannot be modified. Up to 20 custom tags can be added to each resource.

Tagging a Log Group
-------------------

You can add, delete, modify, and view tags on the log group list page. Tags of a log group are synchronized to all log streams in the log group.

#. Log in to the LTS console, and choose **Log Management** in the navigation pane on the left.

#. Move the cursor to the **Tags** column of the target log group and click |image1|.

#. In the **Configure Tag** dialog box displayed, enter a tag key and value, and click **Add**. The entered key and value are then displayed in the *Key*\ =\ *Value* format in the text box.

   .. note::

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click |image2| next to the tag in the text box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.

#. Click **OK**.

   On the **Log Management** page, you can view the added tags in the **Tags** column of the log group.

Tagging a Log Stream
--------------------

You can add, delete, modify, and view tags on the log stream list page. When you manage the tags of a single log stream, the changes will not be synchronized to other streams.

#. Log in to the LTS console, and choose **Log Management** in the navigation pane on the left.

#. Click |image3| before the name of the target log group.

#. Move the cursor to the **Tags** column of the target log stream and click |image4|.

#. In the **Configure Tag** dialog box displayed, enter a tag key and value, and click **Add**. The entered key and value are then displayed in the *Key*\ =\ *Value* format in the text box.

   .. note::

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click |image5| next to the tag in the text box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.

#. Click **OK**.

   In the log stream list, you can view the system tags and added custom tags in the **Tags** column of the log stream.

Tagging a Host Group
--------------------

You can add, delete, modify, and view tags on the host group list page. When you manage the tags of a single host group, the changes will not be synchronized to other groups.

#. Log in to the LTS console, and choose **Host Management** in the navigation pane on the left.

#. On the **Host Groups** tab, click |image6| in the **Operation** column of a host group.

#. In the **Configure Tag** dialog box displayed, enter a tag key and value, and click **Add**. The entered key and value are then displayed in the *Key*\ =\ *Value* format in the text box.

   .. note::

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click |image7| next to the tag in the text box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.

#. Click **OK**.

   On the **Host Management** page, you can view the added tags in the **Tags** column of the host group.

Tagging a Log Ingestion Configuration
-------------------------------------

You can add, delete, modify, and view tags on the log ingestion page. When you manage the tags of a single log ingestion configuration, the changes will not be synchronized to other configurations.

#. Log in to the LTS console, and choose **Log Ingestion** in the navigation pane on the left.

#. Click |image8| in the **Operation** column of a log ingestion configuration.

#. In the **Configure Tag** dialog box displayed, enter a tag key and value, and click **Add**. The entered key and value are then displayed in the *Key*\ =\ *Value* format in the text box.

   .. note::

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click |image9| next to the tag in the text box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.

#. Click **OK**.

   On the **Log Ingestion** page, you can view the added tags in the **Tags** column of the log ingestion configuration.

.. |image1| image:: /_static/images/en-us_image_0000002114655625.png
.. |image2| image:: /_static/images/en-us_image_0000001234565659.png
.. |image3| image:: /_static/images/en-us_image_0000001218081344.png
.. |image4| image:: /_static/images/en-us_image_0000002079093524.png
.. |image5| image:: /_static/images/en-us_image_0000001234365723.png
.. |image6| image:: /_static/images/en-us_image_0000001184322804.png
.. |image7| image:: /_static/images/en-us_image_0000001188807618.png
.. |image8| image:: /_static/images/en-us_image_0000001234565411.png
.. |image9| image:: /_static/images/en-us_image_0000001189126142.png
