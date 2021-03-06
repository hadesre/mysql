# Query backup tasks

You can call the DescribeBackupTasks operation to query the backup tasks of an ApsaraDB for RDS instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Rds&api=DescribeBackupTasks&type=RPC&version=2014-08-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeBackupTasks|The operation that you want to perform. Set the value to **DescribeBackupTasks**. |
|DBInstanceId|String|Yes|rm-uf6wjk5xxxxxxx|The ID of the instance. |
|ClientToken|String|No|ETnLKlblzczshOTUbOCzxxxxxxx|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can only contain ASCII characters and cannot exceed 64 characters in length. |
|Flag|String|No|None|A hidden parameter. |
|BackupJobId|Integer|No|4762614|The ID of the single backup task to query. |
|BackupMode|String|No|Automated|The backup mode that is used by the backup tasks to query. Valid values:

-   **Automated**
-   **Manual** |
|BackupJobStatus|String|No|NoStart|The status of the backup tasks to query. Valid values:

-   **NoStart**: specifies to query the backup tasks that have not started.
-   **Progressing**: specifies to query the backup tasks that are in progress.

This operation returns backup tasks in both states by default. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Items|Array of BackupJob| |An array that consists of backup tasks. |
|BackupJob| | | |
|BackupId|String|346650271|The ID of the backup set that is generated by the backup task.

**Note:** If the returned value of the **BackupStatus** parameter is **Finished**, you must specify the **BackupJobId** parameter to obtain the ID of the generated backup set. |
|BackupJobId|String|4762614|The ID of the backup task. |
|BackupProgressStatus|String|NoStart|The status of the backup program. Valid values:

-   **NoStart**: The backup program has not started.
-   **Preparing**: The backup program is preparing for the backup.
-   **Waiting**: The backup program is waiting.
-   **Uploading**: The backup program is uploading the backup file.
-   **Checking**: The backup program is checking the uploaded backup file.
-   **Finished**: The backup program has finished the backup. |
|BackupStatus|String|NoStart|The status of the backup task. Valid values:

-   **NoStart**: The backup task has not started.
-   **Checking**: The backup task is checking the backup settings.
-   **Preparing**: The backup task is preparing for the backup.
-   **Waiting**: The backup task is waiting.
-   **Uploading**: The backup task is uploading the backup file.
-   **Finished**: The backup task is complete.
-   **Failed**: The backup task failed. |
|JobMode|String|Automated|The mode that is used by the backup task. Valid values:

-   **Automated**
-   **Manual** |
|Process|String|25|The progress of the backup task. Unit: %. |
|TaskAction|String|NormalBackupTask|The type of the backup task. Valid values:

-   **TempBackupTask**: temporary backup task
-   **NormalBackupTask**: regular backup task |
|RequestId|String|90496720-2319-42A8-87CD-FCE4DF95EBED|The ID of the request. |

## Examples

Sample requests

```
http(s)://rds.aliyuncs.com/? Action=DescribeBackupTasks
&DBInstanceId=rm-uf6wjk5xxxxxxx
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeBackupTasksResponse>
      <Items>
            <BackupJob>
                  <JobMode>Automated</JobMode>
                  <BackupProgressStatus>NoStart</BackupProgressStatus>
                  <TaskAction>NormalBackupTask</TaskAction>
                  <BackupStatus>NoStart</BackupStatus>
                  <BackupJobId>4762614</BackupJobId>
            </BackupJob>
      </Items>
      <RequestId>90496720-2319-42A8-87CD-FCE4DF95EBED</RequestId>
</DescribeBackupTasksResponse>
```

`JSON` format

```
{
    "Items": {
        "BackupJob": [
            {
                "JobMode": "Automated",
                "BackupProgressStatus": "NoStart",
                "TaskAction": "NormalBackupTask",
                "BackupStatus": "NoStart",
                "BackupJobId": 4762614
            }
        ]
    },
    "RequestId": "90496720-2319-42A8-87CD-FCE4DF95EBED"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Rds).

