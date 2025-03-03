:original_name: lts_01_0017.html

.. _lts_01_0017:

Glossary
========

This section describes common terms used in LTS to help you better understand and use LTS.

.. table:: **Table 1** Terms

   +--------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Abbreviation | Full Spelling    | Definition                                                                                                                                                                                                                                                                                                                 |
   +==============+==================+============================================================================================================================================================================================================================================================================================================================+
   | LTS          | Log Tank Service | LTS collects, analyzes, and stores logs. You can use LTS for efficient device O&M, service trend analysis, security audits, and monitoring.                                                                                                                                                                                |
   +--------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ``-``        | Log group        | A log group is a group of log streams and is the basic unit for log management in LTS. You need to create a log group before collecting, querying, and transferring logs.                                                                                                                                                  |
   +--------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ``-``        | Log stream       | A log stream is the basic unit for log reads and writes. If there are many logs to collect, you are advised to separate logs into different log streams based on log types, and name log streams in an easily identifiable way.                                                                                            |
   +--------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ``-``        | ICAgent          | ICAgent is the log collection tool of LTS. If you want to use LTS to collect logs from a host, you need to install ICAgent on the host. Batch agent installation is supported if you want to collect logs from multiple hosts. After agent installation, you can check the ICAgent status on the LTS console in real time. |
   +--------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
