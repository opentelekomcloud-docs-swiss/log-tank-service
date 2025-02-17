:original_name: lts_0829.html

.. _lts_0829:

Step 2: Installing ICAgent
==========================

ICAgent is the log collection tool of LTS. Install ICAgent on a host from which you want to collect logs.

If ICAgent has been installed on the host when you use other cloud services, skip the installation.

Prerequisites
-------------

Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host.

Installing ICAgent
------------------

#. Log in to the LTS console and choose **Host Management** in the navigation pane.

#. Click **Install ICAgent** in the upper right corner.

#. Set **OS** to **Linux**.

#. Set **Installation Mode** to **Obtain AK/SK**.

   The Access Key ID/Secret Access Key (AK/SK) can be obtained on the **My Credentials** page. The procedure is as follows:

   a. Hover the mouse pointer over the username in the upper right corner of the page and select **My Credentials**.
   b. On the **My Credentials** page, choose **Access Keys** in the navigation pane on the left.
   c. Click **Create Access Key**, and enter the verification code or password.
   d. Click **OK**, download the generated access key, and keep it secure.

#. Click **Copy Command** to copy the ICAgent installation command.

#. Log in as user **root** to the host (for example, by using a remote login tool such as PuTTY). Run the copied command and enter the obtained AK/SK to install ICAgent.

   When message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status by choosing **Host Management** in the navigation pane of the LTS console and then clicking **Hosts**.
