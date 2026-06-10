:original_name: lts_02_0013.html

.. _lts_02_0013:

Installing ICAgent
==================

ICAgent is a log collection tool for LTS. To use LTS to collect logs from hosts, you need to install ICAgent on the hosts.

Prerequisites
-------------

Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host. If they are inconsistent, errors may occur during log reporting.

Installation Methods
--------------------

There are two methods to install ICAgent.

.. table:: **Table 1** Installation methods

   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Method                                                  | Scenario                                                                                                                  |
   +=========================================================+===========================================================================================================================+
   | Initial installation                                    | You can use this method to install ICAgent on a host that has no ICAgent installed.                                       |
   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Inherited installation (supported only for Linux hosts) | When ICAgent has already been installed on one host but needs to be installed on multiple hosts, you can use this method. |
   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+

Initial Installation (Linux)
----------------------------

#. Log in to the LTS console and choose **Host Management** in the navigation pane.
#. Click **Install ICAgent** in the upper right corner.
#. Set **OS** to **Linux**.
#. Select an installation mode:

   -  Obtain the AK/SK pair. For details, see :ref:`How Do I Obtain an AK/SK Pair? <lts_03_0015>`

      Obtain and use the AK/SK pair of a public account.

      .. important::

         Ensure that the public account and AK/SK pair will not be deleted or disabled. If the AK/SK pair is deleted, ICAgent cannot report data to LTS.

   -  Create an agency. For details, see :ref:`How Do I Install ICAgent by Creating an Agency? <lts_03_0002>`

#. Click **Copy Command** to copy the ICAgent installation command.
#. Log in as user **root** to the host which is deployed in the region same as that you are logged in to (for example, by using a remote login tool such as PuTTY) and run the copied command. If you have chosen **Obtain AK/SK** as the installation mode, enter the AK/SK pair as prompted.

   .. note::

      -  When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status by choosing **Host Management** in the navigation pane of the LTS console and then clicking **Hosts**.
      -  If the installation fails, uninstall ICAgent and reinstall it. If the reinstallation fails, contact technical support.

Inherited Installation (Linux)
------------------------------

Let's assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. You can follow the directions below to install ICAgent on other hosts one by one.

#. Run the following command on the host where ICAgent has been installed, where *x.x.x.x* is the IP address of the host you want to install ICAgent on.

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -ip** *x.x.x.x*

#. Enter the password for user **root** of the host when prompted.

   .. note::

      -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent installation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to remotely communicate with the remote host to install ICAgent.
      -  When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status by choosing **Host Management** in the navigation pane of the LTS console and then clicking **Hosts**.
      -  If the installation fails, uninstall ICAgent and reinstall it. If the reinstallation fails, contact technical support.

Batch Inherited Installation (Linux)
------------------------------------

Let's assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. You can follow the directions below to install ICAgent on other hosts in batches.

.. important::

   -  The hosts must all belong to the same Virtual Private Cloud (VPC) and be on the same subnet.
   -  **Python 3.\*** is required for batch installation. If you are prompted that Python cannot be found during ICAgent installation, install Python of a proper version and try again.

**Prerequisites**

The IP addresses and passwords of all hosts to install ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space, as shown in the following example:

**192.168.0.109** *Password* (Replace the IP address and password with the actual ones)

**192.168.0.39** *Password* (Replace the IP address and password with the actual ones)

.. note::

   -  The **iplist.cfg** file contains sensitive information. You are advised to clear it after using it.

   -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

**Procedure**

#. Run the following command on the host that has ICAgent installed:

   .. code-block::

      bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -batchModeConfig /opt/ICAgent/iplist.cfg

   Enter the default password for user **root** of the hosts to install ICAgent. If the passwords of all hosts have been configured in the **iplist.cfg** file, press **Enter** to skip this step.

   .. code-block::

      batch install begin
      Please input default passwd:
      send cmd to 192.168.0.109
      send cmd to 192.168.0.39
      2 tasks running, please wait...
      2 tasks running, please wait...
      2 tasks running, please wait...
      End of install agent: 192.168.0.39
      End of install agent: 192.168.0.109
      All hosts install icagent finish.

   If the message "All hosts install icagent finish." is displayed, ICAgent has been installed on all the hosts listed in the configuration file.

#. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the :ref:`ICAgent status <lts_04_0013>`.
