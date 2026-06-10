:original_name: lts_04_0216.html

.. _lts_04_0216:

Reporting Logs
==============

Function
--------

This API is used to report tenant logs from a host to LTS.

To obtain the access IP address, log in to the LTS console, choose **Host Management** in the navigation pane, and click **Install ICAgent** in the upper right corner. The access IP address is contained in the ICAgent installation command. The port number is 8102. You can check the :ref:`Example Request <lts_04_0216__en-us_topic_0000001144886981_en-us_topic_0000001132657761_section1475015224126>` to see how to add the access IP address and port number in a request.

URI
---

POST /v2/{project_id}/lts/groups/{log_group_id}/streams/{log_stream_id}/tenant/contents

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain it, see "Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID" in *Log Tank Service API Reference*.    |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_group_id    | Yes             | String          | Log group ID. For details about how to obtain it, see "Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID" in *Log Tank Service API Reference*.  |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_stream_id   | Yes             | String          | Log stream ID. For details about how to obtain it, see "Obtaining the Account ID, Project ID, Log Group ID, and Log Stream ID" in *Log Tank Service API Reference*. |
   |                 |                 |                 |                                                                                                                                                                     |
   |                 |                 |                 | **A write rate exceeding 100 MB/s per log stream may cause log losses.**                                                                                            |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+-----------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                               |
   +==============+===========+========+===========================================================+
   | X-Auth-Token | Yes       | String | Indicates the user token obtained from IAM.               |
   +--------------+-----------+--------+-----------------------------------------------------------+
   | Content-Type | Yes       | String | Set this parameter to **application/json;charset=UTF-8**. |
   +--------------+-----------+--------+-----------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                             |
   +===================+=================+=================+=========================================================================================================================================================================+
   | log_time_ns       | Yes             | Long            | Time when log data is reported (UTC time in nanoseconds).                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                         |
   |                   |                 |                 | .. note::                                                                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                         |
   |                   |                 |                 |    Logs reported to LTS through APIs are retained for two days (from the log reporting time to the current time). Logs reported more than two days ago will be deleted. |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | contents          | Yes             | Array of String | Indicates the log content.                                                                                                                                              |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | labels            | Yes             | Object          | Custom labels.                                                                                                                                                          |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_project_id | No              | String          | Tenant ID.                                                                                                                                                              |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

When the status code is **200**, the response parameters are as follows:

.. table:: **Table 4** Response body parameters

   ============ ====== ================
   Parameter    Type   Description
   ============ ====== ================
   errorCode    String Error code.
   errorMessage String Error message.
   result       String Response result.
   ============ ====== ================

When the status code is **400**, the response parameters are as follows:

.. table:: **Table 5** Response body parameters

   ============ ====== ================
   Parameter    Type   Description
   ============ ====== ================
   errorCode    String Error code.
   errorMessage String Error message.
   result       String Response result.
   ============ ====== ================

When the status code is **401**, the response parameters are as follows:

.. table:: **Table 6** Response body parameters

   ============ ====== ================
   Parameter    Type   Description
   ============ ====== ================
   errorCode    String Error code.
   errorMessage String Error message.
   result       String Response result.
   ============ ====== ================

When the status code is **500**, the response parameters are as follows:

.. table:: **Table 7** Response body parameters

   ============ ====== ================
   Parameter    Type   Description
   ============ ====== ================
   errorCode    String Error code.
   errorMessage String Error message.
   result       String Response result.
   ============ ====== ================

When the status code is **503**, the response parameter is as follows:

.. table:: **Table 8** Response body parameter

   ========= ====== =====================================
   Parameter Type   Description
   ========= ====== =====================================
   result    String The requested service is unavailable.
   ========= ====== =====================================

.. _lts_04_0216__en-us_topic_0000001144886981_en-us_topic_0000001132657761_section1475015224126:

Example Request
---------------

.. code-block:: text

   POST https://{access_IP_address:8102}/v2/{project_id}/lts/groups/{log_group_id}/streams/{log_stream_id}/tenant/contents

   {
       "log_time_ns": "1586850540000000000",
       "contents": [
           "Fri Feb  1 07:48:04 UTC 2019 0\n",
           "Sat Apr 18 16:04:04 UTC 2019"
       ],
       "labels": {
           "user_tag": "string"
       }
   }

Example Response
----------------

Example response with status code **200**:

Logs are reported.

.. code-block::

   {
     "errorCode": "SVCSTG.ALS.200.200",
     "errorMessage": "Report success.",
     "result": null
   }

Example response with status code **401**:

The authentication information is incorrect or invalid.

.. code-block::

   {
     "errorCode" : "SVCSTG.ALS.403.105",
     "errorMessage" : "Project id is invalid.",
     "result": null
   }

Status Code
-----------

+-------------+-----------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                   |
+=============+===============================================================================================+
| 200         | The request has succeeded.                                                                    |
+-------------+-----------------------------------------------------------------------------------------------+
| 400         | Invalid request. Modify the request based on the description in **error_msg** before a retry. |
+-------------+-----------------------------------------------------------------------------------------------+
| 401         | The authentication information is incorrect or invalid.                                       |
+-------------+-----------------------------------------------------------------------------------------------+
| 500         | An internal error occurred.                                                                   |
+-------------+-----------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable.                                                         |
+-------------+-----------------------------------------------------------------------------------------------+
