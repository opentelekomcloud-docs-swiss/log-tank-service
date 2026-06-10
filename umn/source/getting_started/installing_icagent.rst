:original_name: lts_0829.html

.. _lts_0829:

Installing ICAgent
==================

ICAgent is the log collection tool of LTS. Install ICAgent on a host from which you want to collect logs.

If ICAgent has been installed on the host when you use other cloud services, skip the installation.

Prerequisites
-------------

Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host.


Installing ICAgent
------------------

#. Log in to the LTS console and choose **Host Management** in the navigation pane.

#. Click **Install ICAgent** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000002513862583.png
      :alt: **Figure 1** Installing ICAgent

      **Figure 1** Installing ICAgent

#. Set **OS** to **Linux**.

#. Set **Installation Mode** to **Obtain AK/SK**.

   .. note::

      Ensure that the public account and AK/SK pair will not be deleted or disabled. If the AK/SK pair is deleted, ICAgent cannot report data to LTS.

   Obtain and use the AK/SK pair of a public account.

   The Access Key ID/Secret Access Key (AK/SK) can be obtained on the **My Credentials** page. The procedure is as follows:

   a. Hover the mouse pointer over the username in the upper right corner of the page and select **My Credentials**.
   b. On the **My Credentials** page, choose **Access Keys**.
   c. Click **Create Access Key** and enter a description.

      .. note::

         Up to two access keys can be created for each user. An access key can be downloaded only right after it is created. If the **Create Access Key** button is grayed out, delete an access key first before creating one.

   d. Click **OK**, download the AK/SK pair, and keep it secure.

#. Click **Copy Command** to copy the ICAgent installation command.

#. Log in as user **root** to the host (for example, by using a remote login tool such as PuTTY). Run the copied command and enter the obtained AK/SK pair to install ICAgent.

   When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status by choosing **Host Management** in the navigation pane of the LTS console and then clicking **Hosts**.
