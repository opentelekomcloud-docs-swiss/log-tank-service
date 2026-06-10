:original_name: lts_04_0015.html

.. _lts_04_0015:

Permissions Management
======================

You can use `Identity and Access Management (IAM) <https://docs.sc.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html>`__ for fine-grained permissions control for your LTS. With IAM, you can:

-  Create IAM users for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing LTS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or a cloud service to perform efficient O&M on your LTS resources.

If your account does not require individual IAM users, you can skip this section.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <lts_04_0015__en-us_topic_0191978428_fig1591121431319>`).

Prerequisites
-------------

Before granting permissions to user groups, learn about system-defined permissions in :ref:`Permissions Management <lts-03205>` for LTS.

Process Flow
------------

.. _lts_04_0015__en-us_topic_0191978428_fig1591121431319:

.. figure:: /_static/images/en-us_image_0231061605.png
   :alt: **Figure 1** Process of granting permissions to a user

   **Figure 1** Process of granting permissions to a user

#. .. _lts_04_0015__en-us_topic_0191978428_li1777449128:

   Log in to the IAM console. Create a user group on the IAM console and grant the **LTS FullAccess** permission to the user group. For details, see `Creating a User Group and Assigning Permissions <https://docs.sc.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_group_and_assigning_permissions.html>`__.

   .. note::

      If you select the **LTS FullAccess** permissions, the **Tenant Guest** policy that the permission depends on is automatically selected. You also need to grant the **Tenant Administrator** policy for the global service project to the user group.

#. Create a user on the IAM console and add the user to the user group created in :ref:`1 <lts_04_0015__en-us_topic_0191978428_li1777449128>`. For details, see `Creating a User and Adding the User to a User Group <https://docs.sc.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_and_adding_the_user_to_a_user_group.html>`__.

#. Log in to the console by using the created user and verify permissions in the authorized region. For details, see `Logging In as a User <https://docs.sc.otc.t-systems.com/identity-access-management/umn/getting_started/logging_in_as_a_user.html>`__ and verify permissions.
