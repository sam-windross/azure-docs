---
title: Wait activity
titleSuffix: Azure Data Factory & Azure Synapse
description: The Wait activity in Azure Data Factory and Synapse Analytics pauses the execution of a pipeline for a specified period. 
author: chez-charlie
ms.author: chez
ms.service: data-factory
ms.subservice: orchestration
ms.custom: synapse
ms.topic: conceptual
ms.date: 09/09/2021
---

# Execute wait activity in Azure Data Factory and Synapse Analytics
When you use a Wait activity in a pipeline, the pipeline waits for the specified period of time before continuing with execution of subsequent activities. 

[!INCLUDE[appliesto-adf-asa-md](includes/appliesto-adf-asa-md.md)]


## Syntax

```json
{
    "name": "MyWaitActivity",
    "type": "Wait",
    "typeProperties": {
        "waitTimeInSeconds": 1
    }
}

```

## Type properties

Property | Description | Allowed values | Required
-------- | ----------- | -------------- | --------
name | Name of the `Wait` activity. | String | Yes
type | Must be set to **Wait**. | String | Yes
waitTimeInSeconds | The number of seconds that the pipeline waits before continuing with the processing. | Integer | Yes

## Example

> [!NOTE]
> This section provides JSON definitions and sample PowerShell commands to run the pipeline. For a walkthrough with step-by-step instructions to create a pipeline by using Azure PowerShell and JSON definitions, see [tutorial: create a data factory by using Azure PowerShell](quickstart-create-data-factory-powershell.md).

### Pipeline with Wait activity
In this example, the pipeline has two activities: **Until** and **Wait**. The Wait activity is configured to wait for one second. The pipeline runs the Web activity in a loop with one second waiting time between each run. 

```json
{
    "name": "DoUntilPipeline",
    "properties": {
        "activities": [
            {
                "type": "Until",
                "typeProperties": {
                    "expression": {
                        "value": "@equals('Failed', coalesce(body('MyUnauthenticatedActivity')?.status, actions('MyUnauthenticatedActivity')?.status, 'null'))",
                        "type": "Expression"
                    },
                    "timeout": "00:00:01",
                    "activities": [
                        {
                            "name": "MyUnauthenticatedActivity",
                            "type": "WebActivity",
                            "typeProperties": {
                                "method": "get",
                                "url": "https://www.fake.com/",
                                "headers": {
                                    "Content-Type": "application/json"
                                }
                            },
                            "dependsOn": [
                                {
                                    "activity": "MyWaitActivity",
                                    "dependencyConditions": [ "Succeeded" ]
                                }
                            ]
                        },
                        {
                            "type": "Wait",
                            "typeProperties": {
                                "waitTimeInSeconds": 1
                            },
                            "name": "MyWaitActivity"
                        }
                    ]
                },
                "name": "MyUntilActivity"
            }
        ]
    }
}

```

## Next steps
See other supported control flow activities: 

- [If Condition Activity](control-flow-if-condition-activity.md)
- [Execute Pipeline Activity](control-flow-execute-pipeline-activity.md)
- [For Each Activity](control-flow-for-each-activity.md)
- [Get Metadata Activity](control-flow-get-metadata-activity.md)
- [Lookup Activity](control-flow-lookup-activity.md)
- [Web Activity](control-flow-web-activity.md)
- [Until Activity](control-flow-until-activity.md)
