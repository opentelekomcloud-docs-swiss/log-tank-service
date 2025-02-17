:original_name: lts_08302.html

.. _lts_08302:

Step 3: Ingesting Logs to Log Streams
=====================================

The following shows how you can ingest host logs to LTS.

When ICAgent is installed, configure the paths of host logs that you want to collect in log streams. ICAgent will pack logs and send them to LTS in the unit of log streams.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed ICAgent.

Procedure
---------

#. Log in to the LTS console and choose **Log Ingestion** in the navigation pane.
#. Click **Elastic Cloud Server (ECS)** to configure log ingestion.
#. Select a log stream.

   a. Select a log group from the drop-down list of **Log Group**. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the drop-down list of **Log Stream**. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: Select Host Group**.

#. Select host groups.

   a. In the host group list, select one or more host groups to collect logs. If there are no desired host groups, click **Create** in the upper left corner of the list. On the displayed **Create Host Group** page, create a host group. For details, see :ref:`Managing Host Groups <lts_02_1033>`.

      .. note::

         You can skip this step and configure host groups after the ingestion configuration is complete. There are two ways to do this:

         -  Choose **Host Management** in the navigation pane, click **Host Groups**, and associate host groups with ingestion configurations.
         -  Choose **Log Ingestion** in the navigation pane, click an ingestion configuration, and make the association on the details page.

   b. Click **Next: Configure Collection**.

#. Configure the collection.

   a. Configure the collection parameters. For details, see :ref:`Configuring the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`.
   b. Click **Submit**.

#. Click **Back to Ingestion Configurations** to check the ingestion details. You can also click **View Log Stream** to view the log stream to which logs are ingested.
