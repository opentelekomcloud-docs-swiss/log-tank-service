:original_name: lts_faq_0070.html

.. _lts_faq_0070:

How Do I Disable Collecting CCE Standard Output Logs to AOM?
============================================================

Symptom
-------

As the products evolve, the default collection of CCE standard output logs to AOM is no longer recommended, but for compatibility with old user habits, the default configuration is not modified. If the default configuration does not meet your requirements, disable it on the LTS console. You are advised to collect CCE standard output logs to LTS for unified log management.

.. note::

   Only when the collection of CCE standard output to AOM is disabled, the CCE standard output configured in LTS will take effect.

Solution
--------

#. Log in to the LTS console and choose **Host Management** in the navigation pane on the left.
#. Choose **Hosts** and click **CCE Cluster**.
#. In the CCE cluster, select the CCE cluster, and disable **Output to AOM**.
#. Click **OK**. After ICAgent is restarted, CCE standard output to AOM is disabled.
