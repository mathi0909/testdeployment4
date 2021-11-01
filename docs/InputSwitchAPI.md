<!-- Generated automatically, DO NOT EDIT! -->
<a name="head.Input_Switch_API"></a>
# Input Switch API

**Version: 1.0**

**Status: :black_circle::white_circle::white_circle:**

InputSwitch interface for Thunder framework.

### Table of Contents

- [Introduction](#head.Introduction)
- [Description](#head.Description)
- [Methods](#head.Methods)

<a name="head.Introduction"></a>
# Introduction

<a name="head.Scope"></a>
## Scope

This document describes purpose and functionality of the InputSwitch interface. It includes detailed specification about its methods provided.

<a name="head.Case_Sensitivity"></a>
## Case Sensitivity

All identifiers of the interfaces described in this document are case-sensitive. Thus, unless stated otherwise, all keywords, entities, properties, relations and actions should be treated as such.

<a name="head.Acronyms,_Abbreviations_and_Terms"></a>
## Acronyms, Abbreviations and Terms

The table below provides and overview of acronyms used in this document and their definitions.

| Acronym | Description |
| :-------- | :-------- |
| <a name="acronym.API">API</a> | Application Programming Interface |
| <a name="acronym.HTTP">HTTP</a> | Hypertext Transfer Protocol |
| <a name="acronym.JSON">JSON</a> | JavaScript Object Notation; a data interchange format |
| <a name="acronym.JSON-RPC">JSON-RPC</a> | A remote procedure call protocol encoded in JSON |

The table below provides and overview of terms and abbreviations used in this document and their definitions.

| Term | Description |
| :-------- | :-------- |
| <a name="term.callsign">callsign</a> | The name given to an instance of a plugin. One plugin can be instantiated multiple times, but each instance the instance name, callsign, must be unique. |

<a name="head.References"></a>
## References

| Ref ID | Description |
| :-------- | :-------- |
| <a name="ref.HTTP">[HTTP](http://www.w3.org/Protocols)</a> | HTTP specification |
| <a name="ref.JSON-RPC">[JSON-RPC](https://www.jsonrpc.org/specification)</a> | JSON-RPC 2.0 specification |
| <a name="ref.JSON">[JSON](http://www.json.org/)</a> | JSON specification |
| <a name="ref.Thunder">[Thunder](https://github.com/WebPlatformForEmbedded/Thunder/blob/master/doc/WPE%20-%20API%20-%20WPEFramework.docx)</a> | Thunder API Reference |

<a name="head.Description"></a>
# Description

InputSwitch JSON-RPC interface.

<a name="head.Methods"></a>
# Methods

The following methods are provided by the InputSwitch interface:

InputSwitch interface methods:

| Method | Description |
| :-------- | :-------- |
| [channel](#method.channel) | Enable or Disable the throughput through the given channel |
| [select](#method.select) | Enable the given channel, disabling all othe channels, whish are not immune |
| [status](#method.status) | Check the status of the requested channel |


<a name="method.channel"></a>
## *channel <sup>method</sup>*

Enable or Disable the throughput through the given channel.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.name | string | Callsign that is the owner of this channel |
| params.enabled | boolean | Enable or disable the throughput of data through this channel |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | null | Always null |

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 22 | ```ERROR_UNKNOWN_KEY``` | Failed to scan |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "InputSwitch.1.channel",
    "params": {
        "name": "WebKitBrowser",
        "enabled": false
    }
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": null
}
```

<a name="method.select"></a>
## *select <sup>method</sup>*

Enable the given channel, disabling all othe channels, whish are not immune.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.name | string | Callsign that is the owner of this channel |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | null | Always null |

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 22 | ```ERROR_UNKNOWN_KEY``` | Failed to scan |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "InputSwitch.1.select",
    "params": {
        "name": "WebKitBrowser"
    }
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": null
}
```

<a name="method.status"></a>
## *status <sup>method</sup>*

Check the status of the requested channel.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.name | string | Callsign that is the owner of this channel |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | array |  |
| result[#] | object |  |
| result[#].name | string | Callsign associated with this channel |
| result[#].enabled | boolean | Is the channel enabled to receive info |

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 22 | ```ERROR_UNKNOWN_KEY``` | Could not find the designated channel |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "InputSwitch.1.status",
    "params": {
        "name": "WebKitBrowser"
    }
}
```

#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": [
        {
            "name": "WebKitBrowser",
            "enabled": false
        }
    ]
}
```

