## SubscribeButton

Type
: Function  

Sender
: SDL

Purpose
: Subscribe mob app to a particular button

### Request
SDL requests HMI to subscribe an application to a `buttonName`.

The request may come for the application being whatever active or in background on HMI (depends on SDL Policy Manager permissions).

During Resumption SDL should restore all button subscriptions for application and send required `SubscribeButton` requests to HMI.

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|appID|Integer|true||
|buttonName|[Common.ButtonName](../../common/enums/#buttonname)|true||

### Response

!!! must
1. Check whether the button subscription can be performed for requested `buttonName`. 
2. Respond to SDL within DefaultTimeout period after successful button subscription.

!!!

#### Parameters
This RPC has no additional parameter requirements.

### Sequence Diagrams
|||
[SubscribeButton](./assets/SubscribeButton.png)
|||

### Example Request

```json
{
    "id": 32,
    "jsonrpc": "2.0",
    "method": "Buttons.SubscribeButton",
    "params": {
        "appID": 680015438,
        "buttonName": "VOLUME_UP"
    }
}
```

### Example Response

```json
{
    "id": 32,
    "jsonrpc": "2.0",
    "result": {
        "code": 0,
        "method": "Buttons.SubscribeButton"
    }
}
```

### Example Error 

```json
{
  "id" : 32,
  "jsonrpc" : "2.0",
  "error" :
  {
    "code" : 22,
    "message" : "An unknown issue occurred ",
    "data" :
    {
      "method" : "Buttons.SubscribeButton"
    }
  }
}
```