:original_name: lts-03202.html

.. _lts-03202:

Basic Functions
===============

Real-time Log Collection
------------------------

LTS collects real-time logs and displays them on the LTS console in an intuitive and orderly manner. You can query logs or transfer logs for long-term storage.

Collected logs can be structured for analysis. To be specific, LTS extracts logs that are in a fixed format or share a similar pattern based on the extraction rules you set. Then you can use SQL syntax to query the structured logs.

Log Query and Real-Time Analysis
--------------------------------

Collected logs can be quickly queried by keyword or fuzzy match. You can analyze real-time logs for security diagnosis and analysis, or obtain operations statistics, such as cloud service visits and clicks.

Log Transfer
------------

Logs reported from hosts and cloud services are retained in LTS for seven days by default. Logs older than the retention period will be automatically deleted. For long-term storage, you can transfer logs to Object Storage Service (OBS). Log transfer is to replicate logs to the target cloud service. It means that, after log transfer, the original logs will still be retained in LTS until the configured retention period ends.
