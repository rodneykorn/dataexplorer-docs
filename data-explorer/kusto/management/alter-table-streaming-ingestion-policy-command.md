---
title: ".alter table streaming ingestion policy command - Azure Data Explorer"
description: "This article describes the .alter table streaming ingestion policy command in Azure Data Explorer."
ms.reviewer: yonil
ms.topic: reference
ms.date: 02/21/2023
---
# .alter table streaming ingestion policy

Change the table streaming policy ingestion. Use the [streaming policy](../management/streamingingestionpolicy.md) to manage streaming ingestion for databases and tables.  

Use in low latency scenarios, where ingestion time is less than 10 seconds for varying data volume. You can optimize processing for many tables in one or more databases, when tables receive a few records per second, whereas the ingestion volume is thousands of records per second.

Use the classic bulk ingestion instead of streaming ingestion when the amount of data grows to more than 4 Gb per hour per table. 

* To learn how to implement streaming ingestion, see  [streaming policy](../management/streamingingestionpolicy.md).

## Permissions

You must have at least [Table Admin](access-control/role-based-access-control.md) permissions to run this command.

## Syntax

`.alter` `table` *TableName* `policy` `streamingingestion` *PolicyObject*

## Arguments

- *TableName* - Specify the name of the table. 
- *PolicyObject* - Define a policy object, see also [streaming ingestion](../../ingest-data-streaming.md).

## Returns

Returns a JSON representation of the policy.

## Example

Enable streaming ingestion and determine the suggested allocation rate for the table:

```kusto
.alter table Table1 policy streamingingestion '{"IsEnabled": true, "HintAllocatedRate": 2.1}'
```
