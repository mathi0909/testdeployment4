<!-- Generated automatically, DO NOT EDIT! -->
<a name="head.Location_Sync_API"></a>
# Location Sync API

**Version: 1.0**

**Status: :black_circle::white_circle::white_circle:**

LocationSync interface for Thunder framework.

### Table of Contents

- [Introduction](#head.Introduction)
- [Description](#head.Description)
- [Methods](#head.Methods)
- [Properties](#head.Properties)
- [Notifications](#head.Notifications)

<a name="head.Introduction"></a>
# Introduction

<a name="head.Scope"></a>
## Scope

This document describes purpose and functionality of the LocationSync interface. It includes detailed specification about its methods and properties provided, as well as notifications sent.

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

Location Sync JSON-RPC interface.

<a name="head.Methods"></a>
# Methods

The following methods are provided by the LocationSync interface:

LocationSync interface methods:

| Method | Description |
| :-------- | :-------- |
| [sync](#method.sync) | Synchronizes the location |


<a name="method.sync"></a>
## *sync <sup>method</sup>*

Synchronizes the location.

### Parameters

This method takes no parameters.

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | null | Always null |

### Errors

| Code | Message | Description |
| :-------- | :-------- | :-------- |
| 1 | ```ERROR_GENERAL``` | Failed to synchdonize the location |
| 2 | ```ERROR_UNAVAILABLE``` | Unavailable locator |
| 15 | ```ERROR_INCORRECT_URL``` | Incorrect URL |
| 12 | ```ERROR_INPROGRESS``` | Probing in progress |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "LocationSync.1.sync"
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

<a name="head.Properties"></a>
# Properties

The following properties are provided by the LocationSync interface:

LocationSync interface properties:

| Property | Description |
| :-------- | :-------- |
| [location](#property.location) <sup>RO</sup> | Location information |


<a name="property.location"></a>
## *location <sup>property</sup>*

Provides access to the location information.

> This property is **read-only**.

### Value

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| (property) | object | Location information |
| (property).city | string | City name |
| (property).country | string | Country name |
| (property).region | string | Region name |
| (property).timezone | string | Time zone information |
| (property).publicip | string | Public IP |

### Example

#### Get Request

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "method": "LocationSync.1.location"
}
```

#### Get Response

```json
{
    "jsonrpc": "2.0",
    "id": 42,
    "result": {
        "city": "Wroclaw",
        "country": "Poland",
        "region": "Wroclaw",
        "timezone": "CET-1CEST,M3.5.0,M10.5.0/3",
        "publicip": "78.11.117.118"
    }
}
```

<a name="head.Notifications"></a>
# Notifications

Notifications are autonomous events, triggered by the internals of the implementation, and broadcasted via JSON-RPC to all registered observers. Refer to [[Thunder](#ref.Thunder)] for information on how to register for a notification.

The following events are provided by the LocationSync interface:

LocationSync interface events:

| Event | Description |
| :-------- | :-------- |
| [locationchange](#event.locationchange) | Signals a location change |


<a name="event.locationchange"></a>
## *locationchange <sup>event</sup>*

Signals a location change.

### Parameters

This event carries no parameters.

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.locationchange"
}
```

