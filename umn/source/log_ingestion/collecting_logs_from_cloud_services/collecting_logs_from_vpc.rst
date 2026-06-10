:original_name: lts_04_0305.html

.. _lts_04_0305:

Collecting Logs from VPC
========================

LTS can collect logs from Virtual Private Cloud (VPC).

Procedure
---------

Perform the following operations to configure VPC log ingestion:

#. Log in to the LTS console.

#. Choose **Log Ingestion** in the navigation pane. On the displayed page, click **VPC (Virtual Private Cloud)**.

#. Select a log stream.

   a. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.
   b. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.
   c. Click **Next: Configure VPC**.

#. Configure VPC.

   Click **Configure VPC**.

   a. On the VPC console, choose **VPC Flow Logs**.
   b. On the **VPC Flow Logs** page, click **Create VPC Flow Log** and configure parameters.
   c. Click **OK**.

#. Click **Next: Configure Log Stream**.

   .. table:: **Table 1** Log stream parameters

      +--------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Description                                                                                                                                                                                                             |
      +==========================+=========================================================================================================================================================================================================================+
      | Auto Structure and Index | If this function is enabled, structuring and indexing are automatically configured for the log stream. The structuring is based on the VPC template, and the indexing enables quick analysis for all parsed VPC fields. |
      +--------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Submit**.
