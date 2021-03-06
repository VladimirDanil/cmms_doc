# Create WorkOrderTask Api

A work order consists of a set of tasks that must be executed by some assigned users on a set of assets. This object represents those tasks.

Create a WorkOrderTask if  WorkOrderTask does not already exist.

**URL** : `/api/workordertask`

**Method** : `POST`

**Auth required** : `YES`

**Header** : `Authorization:{jwt-token}`

| Param       |Type     | Description     | 
| :------------- |  :----------- |----------- |
|  intWorkOrderID | Integer    | The ID of the work order the task is part of. For getting possible values, please refer to the WorkOrder section.|
|  intTaskType | Integer    | An integer representing the type of the task. Possible values are : 0 for General, 1 for Text Result, 2 for Meter Reading, and 3 for Inspection Task.|
|  strResult | String    | In case of a Text Result task, a text explaining the output of the task.|
|  intAssetID | Integer    | The ID of the asset the task should be executed on. For getting possible values, please refer to the Asset section.|
|  intOrder | Integer    |An integer used for ordering the tasks inside the work order.|
|  dtmStartDate | timestamp    |The date and time when the task is scheduled to be worked on.|
|  dtmDateCompleted | timestamp    | The date and time when the task was completed.|
|  intCompletedByUserID | Integer    |The ID of the user who competed the task. For getting possible values, please refer to the User section.|
|  intAssignedToUserID | Integer|The ID of the user the task is assigned to. For getting possible values, please refer to the User section.|
|  dblTimeSpentHours | Double|The actual hours that were spent on the task.|
|  intMeterReadingUnitID | Double| In case of a Meter Reading task, the ID of the unit used for the meter reading. For getting all possible values, please refer to the MeterReadingUnit section.|
|  strDescription | String|A short description of the task itself.|
|  strTaskNotesCompletion | String|This field can be used to store some notes upon the completion of the task.|
|  intTaskGroupControlID | Integer|An integer representing the id of the task group.|
|  intParentWorkOrderTaskID | Integer|An integer representing the id of the parent work order task.|

## Success Response
**Code** : `200 success`

**Resonse example**

```json
{
   "msg": "Created successfully!",
    "data": {id: "12"}
    }
```

## Error Responses

**Code** : `401 Unauthorized`

**Condition** : Missing or incorrect authentication credentials and expired one.

**Resonse example**

```json
{
    "msg": "JWT token varified failed!",
    "data":null
}
```

```json
{
    "msg": "JWT token expired!",
    "data":null
}
```

**Condition** : If fields are missed or put the wrong type of value.

**Code** : `400 BAD REQUEST`

**Content example**

```json
{
    "msg": "Create failed"
}
```
