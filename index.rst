.. title:: Nutanix Era Bootcamp 

.. toctree::
  :maxdepth: 2
  :caption: Era Bootcamp
  :name: _era_bootcamp
  :hidden:

  era/era

.. toctree::
  :maxdepth: 2
  :caption: Era Setup Labs
  :name: _era_setup_labs
  :hidden:

  era_deploy_and_register/era_deploy_and_register

.. toctree::
  :maxdepth: 2
  :caption: Era Oracle Labs
  :name: _era_oracle_labs
  :hidden:

  deploy_oracle/deploy_oracle
  deploy_oracle_era/deploy_oracle_era
  patching_oracle/patching_oracle
  admin_oracle/admin_oracle

.. toctree::
  :maxdepth: 2
  :caption: Era Postgres Labs
  :name: _era_postgres_labs
  :hidden:

  era_provision_postgresdb/era_provision_postgresdb
  era_clone_postgresdb/era_clone_postgresdb

.. toctree::
  :maxdepth: 2
  :caption: Era MSSQL Labs
  :name: _era_mssql_labs
  :hidden:

  era_create_mssql_server/era_create_mssql_server
  era_register_mssql_dbs/era_register_mssql_dbs
  era_clone_mssqldb/era_clone_mssqldb

.. toctree::
  :maxdepth: 2
  :caption: Era Rest APIs
  :name: _era_rest_apis
  :hidden:

  era_rest_api/era_rest_api

.. toctree::
  :maxdepth: 2
  :caption: Optional Labs
  :name: _optional_labs
  :hidden:



.. toctree::
  :maxdepth: 2
  :caption: Appendix
  :name: _appendix
  :hidden:

  appendix/glossary
  tools_vms/windows_tools_vm
  tools_vms/linux_tools_vm

.. _getting_started:

---------------
Getting Started
---------------

Welcome to the Nutanix Era Bootcamp!

Nutanix Era is a software suite that automates and simplifies database administration – bringing One Click simplicity and invisible operations to database provisioning and lifecycle management (LCM).

With One Click database provisioning and Copy Data Management (CDM) as its first services, Nutanix Era enables DBAs to provision, clone, refresh, and backup their databases to any point in time. Line of business applications in every vertical depend on databases, providing use cases in both production and non-production environments.

This workbook accompanies an instructor-led session that introduces Nutanix Era and many common management tasks. Each section has a lesson and an exercise to give you hands-on practice. The instructor explains the exercises and answers any additional questions that you may have.

What's New
++++++++++

- Workshop updated for the following software versions:
    - AOS & PC 5.10.x

- Optional Lab Updates:

Resources
+++++++++

- `Era Software Download <https://portal.nutanix.com/page/downloads?product=era>`_
- `Era User Guide <https://portal.nutanix.com/page/documents/details?targetId=Nutanix-Era-User-Guide-v2_0:Nutanix-Era-User-Guide-v2_0>`_

Agenda
++++++

- Nutanix Era Labs
    - Era: Deploy and Register
    - Era: Deploy Oracle DB
    - Era: Patching Oracle DB
    - Era: Admin Oracle DB
    - Era: Provision Postgres DB
    - Era: Clone Postgres DB
    - Era: Create MSSQL Server
    - Era: Register MSSQL Databases
    - Era: Clone MSSQL DB
    - Era: REST API Explorer

- Optional Labs
    - SSHKey Creation

Introductions
+++++++++++++

- Name
- Familiarity with Nutanix

Initial Setup
+++++++++++++

- Take note of the *Passwords* being used.
- Log into your virtual desktops (connection info below)

VPN Access Instructions
+++++++++++++++++++++++

Pulse Secure VPN Client
.......................

#. If you already installed Pulse Secure VPN, you can skip to step 5.
#. to download client use direct download link and Username & Password provided at below.
  - Direct Download\
     - `Windows 32 bit <https://noc.rmutp.ac.th/wp-content/uploads/32bitinstaller.msi>`_
     - `Windows 64 bit <https://noc.rmutp.ac.th/wp-content/uploads/64bitinstaller.msi>`_
     - `Mac OS <https://noc.rmutp.ac.th/wp-content/uploads/macinstaller.dmg>`_

#. Download and install client
#. Logout of the Web UI
#. Open client then ADD connection folowing:\
    - **Type:** Policy Secure (UAC) or Connection Server(VPN)\
    - **Name:** X-Labs - PHX
    - **Server URL:** xlv-uswest1.nutanix.com

#. Once setup, login with the supplied credentials

.. list-table::
  :widths: 20 20 20 20 20
  :header-rows: 1

  * - 
    - Cluster 1
    - Cluster 2
    - Cluster 3
    - Cluster 4
  * - UserName
    - PHX-POC206-User01, ..., PHX-POC206-User20
    - PHX-POC210-User01, ..., PHX-POC210-User20
    - PHX-POC214-User01, ..., PHX-POC214-User20
    - PHX-POC219-User01, ..., PHX-POC219-User20
  * - Password
    - nx2Tech328!
    - nx2Tech809!
    - nx2Tech013!
    - nx2Tech678!

Environment Details
+++++++++++++++++++

Nutanix Workshops using Nutanix Hosted POC environment. All necessary prepared for Labs e.g. images, networks, and VMs.

.. list-table::
  :widths: 20 20 20 20 20
  :header-rows: 1

  * - 
    - Cluster 1
    - Cluster 2
    - Cluster 3
    - Cluster 4
  * - Cluster Name
    - PHX-POC206
    - PHX-POC210
    - PHX-POC214
    - PHX-POC219
  * - Cluster IP
    - http://10.38.206.37
    - http://10.38.210.37
    - http://10.38.214.37
    - http://10.38.219.37
  * - PC IP
    - http://10.38.206.39
    - http://10.38.210.39
    - http://10.38.214.39
    - http://10.38.219.39
  * - PE/PC Username
    - admin
    - admin
    - admin
    - admin
  * - PE/PC Password
    - nx2Tech328!
    - nx2Tech809!
    - nx2Tech013!
    - nx2Tech678!
  * - CVM Username
    - nutanix
    - nutanix
    - nutanix
    - nutanix
  * - CVM Password
    - nx2Tech328!
    - nx2Tech809!
    - nx2Tech013!
    - nx2Tech678!

Each cluster has a dedicated domain controller VM, **DC**, responsible for providing AD services for the **NTNXLAB.local** domain. The domain is populated with the following Users and Groups:

.. list-table::
  :widths: 25 35 40
  :header-rows: 1

  * - Group
    - Username(s)
    - Password
  * - Administrators
    - Administrator
    - nutanix/4u
  * - SSP Admins
    - adminuser01-adminuser25
    - nutanix/4u
  * - SSP Developers
    - devuser01-devuser25
    - nutanix/4u
  * - SSP Power Users
    - poweruser01-poweruser25
    - nutanix/4u
  * - SSP Basic Users
    - basicuser01-basicuser25
    - nutanix/4u
