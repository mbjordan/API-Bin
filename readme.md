# API Bin

API Bin is a RESTful web service built in a Key->Value model where the key is used to return the value (duh).

## Get a resource

    /get/resource-key

### Adding a callback function:

    /get/resource-key?callback=whatever

### Wrapping resource results in quotes:

    /get/resource-key?qwrap=(double|single)

* Use `double` to wrap results in double quotes
* Use `single` to wrap results in single quotes

### Defining a content type:

    /get[/content-type]/resource-key

To define a specific content type, one of the optional parameters (below) must be passed after `/get`. So a JSON get request would look like `/get/json/resource-key`

* js returns text/javascript; charset=utf-8
* text returns text/plain; charset=utf-8
* json returns application/json; charset=utf-8
* xml returns text/xml; charset=utf-8

---

## Set a resource

    /set (HTTP GET/HTTP POST)

Calling `/set` via HTTP GET will return the GUI for browser use.

Calling `/set` via HTTP POST will require two POST fields:

* `key` - The resource key
* `value` - The resource data

## Edit a resource

    /edit/resource-key

This is GUI only at the moment.