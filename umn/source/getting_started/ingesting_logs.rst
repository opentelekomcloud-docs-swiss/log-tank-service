:original_name: lts_08302.html

.. _lts_08302:

Ingesting Logs
==============

The following shows how you can ingest host logs to LTS.

When ICAgent is installed, configure the paths of host logs that you want to collect in log streams. ICAgent will pack logs and send them to LTS in the unit of log streams.

Prerequisites
-------------

-  You have created log groups and log streams.
-  You have installed ICAgent.

Procedure
---------

#. Log in to the LTS console and choose **Log Ingestion** in the navigation pane.

#. Click **ECS (Elastic Cloud Server)** to configure log ingestion.

#. Select a log stream.

   a. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: (Optional) Select Host Group**.

#. Select a host group.

   a. In the host group list, select one or more host groups to collect logs. If there are no desired host groups, click **Create** in the upper left corner of the list. On the displayed **Create Host Group** page, create a host group. For details, see :ref:`Creating a Host Group (IP Address) <lts_02_1033__en-us_topic_0000001118763740_section665755611241>`.

      .. note::

         You can skip this step and configure host groups after the ingestion configuration is complete. There are two options to do this:

         -  On the LTS console, choose **Host Management** > **Host Groups** and associate host groups with ingestion configurations.
         -  On the LTS console, choose **Log Ingestion** in the navigation pane and click an ingestion configuration. On the displayed page, add one or more host groups for association.

   b. Click **Next: Configurations**.

#. Configure the collection.

   For details, see :ref:`Configurations <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`.

#. (Optional) Configure log structuring.

#. (Optional) Configure **Index Settings**.

#. Click **Submit** Click **Back to Ingestion Configurations** to check the ingestion details. You can also click **View Log Stream** to view the log stream to which logs are ingested.
