# Introduction

## About this Workshop

There are several methods to set up and consume data sharing using:

* PL/SQL scripts in Autonomous Database (ADB) using delta sharing protocol
* PL/SQL scripts in Autonomous Database (ADB) using Cloud links
* _Data Studio in Autonomous Database (ADB) using delta sharing protocol_ _**(covered in this workshop)**_
* Data Studio in Autonomous Database (ADB) using Cloud links

<!--- comment --->

Data sharing enables you to share the same data with one or more consumers. Sharing data and consuming data from external sources enables collaboration with partners, establishes new partnerships, and generates new revenue streams with data monetization. The Oracle Data Sharing for general recipients is based on the open _delta sharing standard protocol_, providing a simple REST-based API to share data in `Parquet` format.

Data is made accessible by the data sharing provider (such as Oracle Autonomous Database) to the data sharing recipient (such as Microsoft Power BI) at query time in `Parquet` format. The provider can only share data which they have access to when they log into an ADB instance. The parquet files are physically stored in an OCI bucket or use the bucket to store live share parquet files to cache them and improve performance.

Estimated Workshop Time: 1 hour

### Objectives

In this workshop, you will:

* Set up the workshop environment
* Create a data share provider user that creates and manages the data share and the recipients of the data share
* Create an Object Storage bucket to store the shared data
* Create an OCI credential and associate it with the Object Storage bucket
* Create, populate, and publish a data share
* Create and authorize a data share recipient
* Create a data share consumer and consume the data as a recipient

### Prerequisites

* An Oracle account

### Traditional Methods to Share Data

Some examples of how users traditionally shared data are:

* Send data via email
* Share data through an FTP server
* Use application-specific APIs for data extraction
* Leverage vendor specific tools to copy relevant data

While the traditional methods work in general, they come with certain _drawbacks_:

* Managing separate processes for data extraction, preparation or remote access are labor-intensive.
* Extracting and duplicating data is prone to data staleness.
* Architectures and processes can become very difficult to maintain and hard to scale.
* Redundant data extraction can introduce format compatibility issues.
* Data extraction and preparation must handle sensitive information properly.

### The Modern Way for Sharing Data

Modern data sharing must be open, secure, real-time, vendor-agnostic, and avoid the pitfalls of extracting and duplicating data for individual consumers of data in a collaborative environment. Delta Sharing is an open protocol for secure real-time data exchange of large datasets that satisfies all these criteria, supported by multiple clients and program languages, and vendor agnostic.

The open Delta Sharing protocol is aimed to solve the following problems:

* Share data without copying it to another system
* Producer controls the state of data (version of data)
* Be an open cross-platform solution
* Support a wide range of clients such as Power BI, Tableau, Apache Spark, pandas and Java
* Provide flexibility to consume data using the tools of choice for BI, machine learning and AI use cases
* Provide strong security, auditing, and governance
* Scale to massive data sets

**Important:**    
In this workshop, you will assume the responsibilities of several users. Initially, you will log in as the default ADB **`admin`** user to create a **`share_provider`** user, a **`share_consumer`** user, and to perform various administration tasks. The **`share_provider`** user creates a data share recipient named **`training_recipient`**. In various labs, you will log in as either the **`share_provider`** user or the **`share_consumer`** user to perform the appropriate tasks associated with those users.

**_In real use cases, there will be different users performing different responsibilities._**

   ![The data sharing overview.](images/data-sharing-diagram.png =60%x*)

### How Does Delta Sharing Work?

At the high level, the delta sharing protocol works as follows:

* The share provider user creates and publishes a data share that can be shared with one or more recipients.
* The share provider user creates and authorizes recipients.
* Every recipient will get a personal activation link to download their own `.JSON` profile with the necessary information to access their data share.
* The recipient subscribes to the data share provider by using the .JSON configuration profile.
* The recipient retrieves data from the share.

You may now proceed to the next lab.

## Learn More

* [The Share Tool](https://docs.oracle.com/en/database/oracle/sql-developer-web/sdwad/adp-data-share-tool.html#GUID-7EECE78B-336D-4853-BFC3-E78A7B8398DB)
* [Using Oracle Autonomous Database Serverless](https://docs.oracle.com/en/cloud/paas/autonomous-database/adbsa/index.html)
* [Oracle Cloud Infrastructure Documentation](https://docs.cloud.oracle.com/en-us/iaas/Content/GSG/Concepts/baremetalintro.htm)

## Acknowledgements

* **Author:** Lauran K. Serhal, Consulting User Assistance Developer
* **Contributor:** Alexey Filanovskiy, Senior Product Manager
* **Last Updated By/Date:** Lauran K. Serhal, June 2025

Data about movies in this workshop were sourced from Wikipedia.

Copyright (C) 2025, Oracle Corporation.

Permission is granted to copy, distribute and/or modify this document under the terms of the GNU Free Documentation License, Version 1.3 or any later version published by the Free Software Foundation; with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts. A copy of the license is included in the section entitled [GNU Free Documentation License](https://oracle-livelabs.github.io/adb/shared/adb-15-minutes/introduction/files/gnu-free-documentation-license.txt)
