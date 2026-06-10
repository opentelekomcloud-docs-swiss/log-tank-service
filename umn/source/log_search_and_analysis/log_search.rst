:original_name: lts_05_0005.html

.. _lts_05_0005:

Log Search
==========

Follow the directions below to search logs by keyword and time range:

#. Log in to the LTS console and choose **Log Management** in the navigation pane.

#. In the log group list, click |image1| on the left of a log group name.

#. In the log stream list, click the name of the target log stream.

#. Above the search box, select a time range.

   There are three types of time range: relative time from now, relative time from last, and specified time. Select a time range as required.

   .. note::

      -  From now: queries log data generated in a time range that ends with the current time, such as the previous 1, 5, or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from now, the charts on the dashboard display the log data that is generated from 18:20:31 to 19:20:31.
      -  From last: queries log data generated in a time range that ends with the current time, such as the previous 1 or 15 minutes. For example, if the current time is 19:20:31 and 1 hour is selected as the relative time from last, the charts on the dashboard display the log data that is generated from 18:00:00 to 19:00:00.
      -  **Specified**: queries log data that is generated in a specified time range.

#. On the log stream details page, you can search for logs using the following methods:

   a. In the search area, click the search box, enter a keyword or select a field or keyword from the drop-down list, and click **Search**.

      Logs that contain the keyword are displayed on the **Raw Logs** tab page.

      .. note::

         -  The structuring fields are displayed in **key:value** format.

   b. On the **Raw Logs** page, click a field in blue in the log content. You can select **Copy**, **Add To Search**, and **Exclude from Search** from the displayed drop-down list.

   c. Click a field for which quick analysis has been created to add it to the search box.

      .. note::

         If the field you click already exists in the search box, it will be replaced by this newly added one. If the field is added for the first time, fields in the search box are searched using the AND operator.

   d. In the search area, press the up and down arrows on the keyboard to select a keyword or search syntax from the drop-down list, press **Tab** or **Enter** to select a keyword or syntax, and click **Search**.

#. Under the log content, click |image2| in front of the time. Structured fields can be displayed in table or JSON format.

   -  On the **Table** tab page, you can search for logs by adding a field to a query or excluding a field from a query, or through whether a field exists, whether a field does not exist, or whether a field is hidden. For details, see :ref:`Search Syntax <lts_05_0111>`.
   -  On the **JSON** tab page, you can view or copy a log.

#. Set the layout.

   a. Select **All layouts** from the drop-down list. The layout setting page is displayed. The layout list contains the default layout, pure layout, and default layout of container logs. You can set whether to display fields on the layout.

      **Cloud**: This mode is applicable to users who have the write permission. Layout information is stored on the cloud.

      **Local Cache**: This mode is applicable to users who have only the read permission. Layout information is cached in the local browser.

   b. Click |image3| to add a custom layout and set the layout name and visibility of layout fields.

   c. After the setting is complete, click **OK**. The new custom layout is displayed in the drop-down list.

Common Log Search Operations
----------------------------

Log search operations include sharing logs and refreshing logs.

.. table:: **Table 1** Common operations

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                                                                                                                                                                      |
   +===================================+==================================================================================================================================================================================================================================================================+
   | Interactive search                | Click |image4| in front of the search box. In the displayed **Interactive Search** dialog box, select fields for index configuration, set the filtering mode, and add associations and groups. After the setting is complete, you can preview the search syntax. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Creating quick search criteria    | Click |image5| to create a quick search.                                                                                                                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Sharing logs                      | Click |image6| to copy the link of the current log search page to share the logs that you have searched.                                                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Refreshing logs                   | You can click |image7| to refresh logs in two modes: manual refresh and automatic refresh.                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | -  Manual refresh: Select **Refresh Now** from the drop-down list.                                                                                                                                                                                               |
   |                                   | -  Automatic refresh: Select an interval from the drop-down list to automatically refresh logs. The interval can be 15 seconds, 30 seconds, 1 minute, or 5 minutes.                                                                                              |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Copying logs                      | Click |image8| to copy the log content.                                                                                                                                                                                                                          |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Viewing context of a log          | Click |image9| to view the log context.                                                                                                                                                                                                                          |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Simplifying field details         | Click |image10| to view the simplified field details.                                                                                                                                                                                                            |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Unfold/Fold                       | Click |image11| to display all the log content. Click |image12| to fold the log content.                                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    **Unfold** is enabled by default.                                                                                                                                                                                                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Downloading logs                  | Click |image13|. On the displayed **Download Logs** page, click **Direct Download**.                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | **Direct Download**: Download log files to the local PC. Up to 5,000 logs can be downloaded at a time.                                                                                                                                                           |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | Select **.csv** or **.txt** from the drop-down list and click **Download** to export logs to the local PC.                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    -  If you select **Export .csv**, logs are exported as a table.                                                                                                                                                                                               |
   |                                   |    -  If you select **Export .txt**, logs are exported as a **.txt** file.                                                                                                                                                                                       |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Collapse all/Expand all           | Click |image14| to set the number of lines displayed in the log content. Click |image15| to close it.                                                                                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    By default, logs are not collapsed, and two rows of logs are shown after collapsing. You can display up to six rows.                                                                                                                                          |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | JSON                              | Move the cursor over |image16|, click **JSON**, and set JSON formatting.                                                                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    Formatting is enabled by default. The default number of expanded levels is 2.                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | -  Formatting enabled: Set the default number of expanded levels. Maximum value: **10**.                                                                                                                                                                         |
   |                                   | -  Formatting disabled: JSON logs will not be formatted for display.                                                                                                                                                                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Collapse configuration            | Move the cursor over |image17|, click **Log Collapse**, and set the maximum characters to display in a log.                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | If the number of characters in a log exceeds the maximum, the extra characters will be hidden. Click **Expand** to view all.                                                                                                                                     |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    Logs are collapsed by default, with a default character limit of 400.                                                                                                                                                                                         |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Log time display                  | Move the cursor over |image18| and click **Log time display**. On the page that is displayed, set whether to display milliseconds and whether to display the time zone.                                                                                          |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    By default, the function of displaying milliseconds is enabled.                                                                                                                                                                                               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Virtual Scrolling                 | Move the cursor over |image19| and click **Virtual Scrolling**. On the page that is displayed, set whether to enable virtual scrolling and enter the buffer size.                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | .. note::                                                                                                                                                                                                                                                        |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   |    -  Virtual scrolling eliminates or minimizes frame and page freezing for better user experience.                                                                                                                                                              |
   |                                   |    -  Data is re-rendered during the process. This may affect smoothness.                                                                                                                                                                                        |
   |                                   |    -  The buffer size determines the amount of data that can be loaded simultaneously. The larger the buffer, the more data loaded simultaneously, but the worse the scrolling performance.                                                                      |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Invisible fields (|image20|)      | This list displays the invisible fields configured in the layout settings.                                                                                                                                                                                       |
   |                                   |                                                                                                                                                                                                                                                                  |
   |                                   | -  The |image21| button is unavailable for log streams without layout settings configured.                                                                                                                                                                       |
   |                                   | -  If the log content is **CONFIG_FILE** and layout settings are not configured, the default invisible fields include **appName**, **clusterId**, **clusterName**, **containerName**, **hostIPv6**, **NameSpace**, **podName**, and **serviceID**.               |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001463823649.png
.. |image2| image:: /_static/images/en-us_image_0000001658714928.png
.. |image3| image:: /_static/images/en-us_image_0000001706936781.png
.. |image4| image:: /_static/images/en-us_image_0000001557984216.png
.. |image5| image:: /_static/images/en-us_image_0000001561940610.png
.. |image6| image:: /_static/images/en-us_image_0000001421609924.png
.. |image7| image:: /_static/images/en-us_image_0000001481236306.png
.. |image8| image:: /_static/images/en-us_image_0000001262546024.png
.. |image9| image:: /_static/images/en-us_image_0000001262546228.png
.. |image10| image:: /_static/images/en-us_image_0000001611750029.png
.. |image11| image:: /_static/images/en-us_image_0000001611940613.png
.. |image12| image:: /_static/images/en-us_image_0000001612061257.png
.. |image13| image:: /_static/images/en-us_image_0000001474530441.png
.. |image14| image:: /_static/images/en-us_image_0000001612024421.png
.. |image15| image:: /_static/images/en-us_image_0000001611907193.png
.. |image16| image:: /_static/images/en-us_image_0000001410398388.png
.. |image17| image:: /_static/images/en-us_image_0000001608069337.png
.. |image18| image:: /_static/images/en-us_image_0000001674961080.png
.. |image19| image:: /_static/images/en-us_image_0000001809715517.png
.. |image20| image:: /_static/images/en-us_image_0000001316788136.png
.. |image21| image:: /_static/images/en-us_image_0000001320576858.png
