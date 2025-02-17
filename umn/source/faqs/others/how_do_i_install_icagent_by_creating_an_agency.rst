:original_name: lts_03_0002.html

.. _lts_03_0002:

How Do I Install ICAgent by Creating an Agency?
===============================================

When installing ICAgent, you can create an IAM agency, and ICAgent will automatically obtain an AK/SK pair and generate the ICAgent installation command.

Procedure
---------

#. Log in to the console and choose |image1| > **Management & Deployment** > **Identity and Access Management**.
#. Choose **Agencies** in the navigation pane on the left.
#. Click **Create Agency** in the upper right corner and set parameters as follows:

   .. table:: **Table 1** Agency parameters

      +-----------------+--------------------------------------------------------------------+
      | Parameter       | Description                                                        |
      +=================+====================================================================+
      | Agency Name     | Set the agency name. For example, **lts_ecm_trust**.               |
      +-----------------+--------------------------------------------------------------------+
      | Agency Type     | Select **Cloud service**.                                          |
      +-----------------+--------------------------------------------------------------------+
      | Cloud Service   | Select **Elastic Cloud Server (ECS) and Bare Metal Server (BMS)**. |
      +-----------------+--------------------------------------------------------------------+
      | Validity Period | Select **Unlimited**.                                              |
      +-----------------+--------------------------------------------------------------------+
      | Description     | (Optional) Provide details about the agency.                       |
      +-----------------+--------------------------------------------------------------------+

#. Click **Next**.
#. Add the **LTS Administrator** permissions and click **Next**.
#. Select **Region-specific projects** for **Scope**.
#. Click **OK**. The authorization takes effect 15 to 30 minutes later.

Making an Agency Effective
--------------------------

#. Choose **Service List** > **Computing** > **Elastic Cloud Server**.
#. Click the ECS where ICAgent is installed. The ECS details page is displayed.
#. Select the created agency and confirm the configuration to make the agency effective.

.. |image1| image:: /_static/images/en-us_image_0000001145758035.png
