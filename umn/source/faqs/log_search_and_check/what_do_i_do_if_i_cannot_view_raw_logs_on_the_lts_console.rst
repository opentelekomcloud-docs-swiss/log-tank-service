:original_name: lts_faq_0031.html

.. _lts_faq_0031:

What Do I Do If I Cannot View Raw Logs on the LTS Console?
==========================================================

Symptom
-------

No log events are displayed on the **Raw Logs** tab in a log stream on the LTS console.

Possible Causes
---------------

-  ICAgent has not been installed.
-  The collection path is incorrectly configured.
-  The **Log Collection** function on the LTS console is disabled.
-  The rate of writing logs into log streams or length of single-line logs exceeds what is supported.
-  The browser has slowed down because of the amount of log data.

Solution
--------

-  If ICAgent has not been installed, install it. For details, see :ref:`Installing ICAgent <lts_02_0013>`.
-  If the collection path is set to a directory, for example, **/var/logs/**, only **.log**, **.trace**, and **.out** files in the directory are collected. If the collection path is set to name of a text file, that file is directly collected.
-  Log in to the LTS console, choose **Configuration Center** > **Log Collection**, and enable the **Log Collection** function.
-  If the rate of writing logs into log streams or length of single-line logs exceeds the limit, or the browser has slowed down because of the amount of log data, use Google Chrome or Firefox to query logs.
