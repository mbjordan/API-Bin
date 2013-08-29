# API Bin

> This is a draft of an idea, using [Readme Driven Development](http://tom.preston-werner.com/2010/08/23/readme-driven-development.html) 

API Bin is a RESTful web service built in a Key->Value model where the key is used to return the value (duh). The goal is to easily test API implementations without actually using the API that the implementation was implemented for (phew).

The API is public, with the option to create user accounts to store bins on. A bin related to a user-account can be either private (anyone with link) or public.

Any type of data can be set, and public bins (not associated with an account) will be automatically deleted after (6|12|24) hours to keep key names clear for reuse.

## Set a resource

    [/user-name]/set (HTTP GET/HTTP POST)

Calling `[/user-name]/set` via HTTP GET will return the GUI for browser use.

Calling `[/user-name]/set` via HTTP POST will require either two POST fields:

* `key` - required - The resource key
* `value` - required - The resource data

Additionally, to set a bin on an account, add a few more optional POST fields.

* `account` - optional - Your APIBin user-name
* `bin-key` - optional - Your APIBin API key
* `private` - optional - Should the bin be private? Either `true` or `false`. Defaults to `true`.

## Get a resource

    [/user-name]/get/resource-key

### Adding a callback function:

    [/user-name]/get/resource-key?callback=whatever

### Wrapping resource results in quotes:

    [/user-name]/get/resource-key?qwrap=(double|single)

* Use `double` to wrap results in double quotes
* Use `single` to wrap results in single quotes

### Defining a content type:

    [/user-name]/get[/content-type]/resource-key

To define a specific content type, one of the optional parameters (below) must be passed after `/get`. So a JSON get request would look like `/get/json/resource-key`

* js returns `Content-Type: text/javascript; charset=utf-8`
* text returns `Content-Type: text/plain; charset=utf-8`
* json returns `Content-Type: application/json; charset=utf-8`
* xml returns `Content-Type: text/xml; charset=utf-8`

## Edit a resource

    [/user-name]/edit/resource-key

---

## The Back-end

The back-end of API Bin will be built using Node.js, express.js & MongoDB; so it will be fast. The platform will either be Heroku or NodeJitsu, so it will be reliable.

The entire application will be open-source to promote community development.

---

If you (an awesome reader) have any ideas or suggestions, please create an issue, or comment on an existing issue. Thanks for being awesome!

## License

In this conceptual stage, the idea is licensed under http://creativecommons.org/licenses/by-nc-sa/3.0/

Please attribute any use of the idea to [@matthewbjordan](https://twitter.com/matthewbjordan)