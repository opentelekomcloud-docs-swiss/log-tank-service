:original_name: lts_faq_0072.html

.. _lts_faq_0072:

What Do I Do If I Do Not See a Host with ICAgent Installed?
===========================================================

If a host with ICAgent installed is not displayed on the **Hosts** tab page on the LTS console, perform the following steps:

Prerequisites
-------------

You have logged in to the LTS console.

Procedure
---------

#. When configuring ECS log ingestion, if the ECS is not displayed on the **Hosts** tab page after you install ICAgent on it:

   a. On the **Install ICAgent** page, ensure that the installation command is correctly copied. Do not use the installation command across regions.
   b. Ensure that the obtained AK/SK pair is correct and has not been deleted.
   c. Run the **netstat -nap \| grep icagent** command to check whether the host network is proper.

#. When configuring CCE log ingestion, if the CCE cluster is not displayed on the **Hosts** tab page after you install ICAgent on it:

   Ensure that ICAgent has been installed in the CCE cluster and a host group with custom identifiers has been created for related nodes. If ICAgent has not been installed, upgrade it on the **Host Management** page.
