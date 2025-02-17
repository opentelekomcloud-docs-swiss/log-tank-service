:original_name: lts_faq_0003.html

.. _lts_faq_0003:

What Kinds of Logs Does LTS Collect? What Kinds of Files Does LTS Collect?
==========================================================================

Logs That Can Be Collected by LTS:
----------------------------------

-  Host logs. ICAgent should be installed on the target hosts for log collection.
-  Cloud service logs. To collect logs from cloud services, enable log reporting to LTS on their consoles.

Files That Can Be Collected by LTS:
-----------------------------------

If the collection path is set to a directory, for example, **/var/logs/**, only .log, .trace, and .out files in the directory are collected. If the collection path is set to the name of a file (only text files are supported), the specified file is collected. Note that LTS only collects logs generated in the last 7 days.
