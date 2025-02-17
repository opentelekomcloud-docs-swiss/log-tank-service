:original_name: lts-07211.html

.. _lts-07211:

Log Read/Write
==============

This section describes the restrictions on LTS log read/write.

.. table:: **Table 1** Log read/write restrictions

   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | Category        | Item                       | Description                                                                                                                   | Remarks         |
   +=================+============================+===============================================================================================================================+=================+
   | A complete LTS  | Number of new logs per day | The volume of new logs per day in a complete LTS is limited by the AOM specifications you purchased.                          | N/A             |
   |                 |                            |                                                                                                                               |                 |
   |                 |                            | -  Small specifications: up to 42 GB/day                                                                                      |                 |
   |                 |                            | -  Medium specifications: up to 126 GB/day                                                                                    |                 |
   |                 |                            | -  Large specifications: up to 250 GB/day                                                                                     |                 |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Steady log rate            | Steady log rate = Number of new logs per day/24 hours/3600 seconds                                                            |                 |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Peak log rate              | Peak log rate = 2 x steady log rate                                                                                           |                 |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log writes                 | The number of writes is less than 1000 or the number of new logs per day/1 TB x 1000 (whichever is larger) in a complete LTS. | N/A             |
   |                 |                            |                                                                                                                               |                 |
   |                 |                            | The maximum number of log writes is 10,000 per second.                                                                        |                 |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log query                  | Up to 10 MB of logs are returned in a single API query in a complete LTS.                                                     | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log reads                  | Logs can be read up to 600 times per minute in a complete LTS.                                                                | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | Log group       | Number of new logs per day | The total number of new logs in all log groups cannot exceed the limit set in a complete LTS.                                 | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Steady log rate            | The total number of new logs in all log groups cannot exceed the limit set in a complete LTS.                                 | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Peak log rate              | The total number of new logs in all log groups cannot exceed the limit set in a complete LTS.                                 | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log reads                  | Logs are read up to 500 times per minute in a log group.                                                                      | N/A             |
   |                 |                            |                                                                                                                               |                 |
   |                 |                            | N/A                                                                                                                           |                 |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log writes                 | The total number of new logs in all log groups cannot exceed the limit set in a complete LTS.                                 | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log query                  | Up to 10 MB of logs are returned in a single API query for a log group.                                                       | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log reads                  | The total number of new logs in all log groups cannot exceed the limit set in a complete LTS.                                 | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   | Log stream      | Number of new logs per day | The total number of new logs in all log streams cannot exceed the limit set in a complete LTS.                                | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Steady log rate            | The total number of new logs in all log streams cannot exceed the limit set in a complete LTS.                                | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Peak log rate              | The total number of new logs in all log streams cannot exceed the limit set in a complete LTS.                                | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log writes                 | The total number of new logs in all log streams cannot exceed the limit set in a complete LTS.                                | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log query                  | Up to 10 MB of logs are returned in a single API query for a log stream.                                                      | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log reads                  | The total number of new logs in all log streams cannot exceed the limit set in a complete LTS.                                | N/A             |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
   |                 | Log time                   | Logs in a period of 48 hours can be collected. Logs generated 48 hours before or after the current time cannot be collected.  | N/A             |
   |                 |                            |                                                                                                                               |                 |
   |                 |                            | For example:                                                                                                                  |                 |
   |                 |                            |                                                                                                                               |                 |
   |                 |                            | -  If the current time is 11:00 on January 7, 2022, logs generated before 11:00 on January 5 cannot be collected.             |                 |
   |                 |                            | -  If the current time is 11:00 on January 7, 2022, logs generated after 11:00 on January 9 cannot be collected.              |                 |
   +-----------------+----------------------------+-------------------------------------------------------------------------------------------------------------------------------+-----------------+
