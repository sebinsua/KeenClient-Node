# Keen IO - NodeJS

[![Build Status](https://travis-ci.org/keenlabs/KeenClient-Node.png)](https://travis-ci.org/keenlabs/KeenClient-Node)

Keen IO is an online service to collect, analyze, and visualize your data.

## Getting Started

`npm install keen.io`

## Examples

### Initialisation

```javascript
var keen = require('keen.io');

// Configure instance. Only projectId and writeKey are required to send data.
var keen = keen.configure({
	projectId: "<project_id>",
	writeKey: "<write_key>",
	readKey: "<read_key>",
	masterKey: "<master_key>"
});
```

You can also have multiple instances if you are connecting to multiple KeenIO accounts in the one project (probably edge case).

```javascript
var keen = require('keen.io');

// Configure instance with API Key
var keen1 = keen.configure({...});
var keen2 = keen.configure({...});
```

In the future there will be the ability to pass options into the initialisation such as batching inserts, etc. The structure of this hasn't been defined yet but will look something like the following.

```javascript
var keen = require('keen.io');

// Configure instance with API Key and options
var keen = keen.configure({ 
	projectId: "<project_id>",
	batchEventInserts: 30 
});
```

### Send Events

```javascript
var keen = require("keen.io");
var keen = keen.configure({
	projectId: "<project_id>",
	writeKey: "<write_key>"
});

// send single event to Keen IO
keen.addEvent("my event collection", {"property name": "property value"}, function(err, res) {
	if (err) {
		console.log("Oh no, an error!");
	} else {
		console.log("Hooray, it worked!");
	}
});

// send multiple events to Keen IO
keen.addEvents({
	"my first event collection": [{"property name": "property value"}, ...],
	"my second event collection": [{"property name2": "property value 2"}]
}, function(err, res) {
	if (err) {
		console.log("Oh no, an error!");
	} else {
		console.log("Hooray, it worked!");
	}
});
```

## Future Updates

Future module updates are planned to introduce the remaining api calls. You can see some of the spec for that in examples/queries.js. Also as mentioned above specifying options when creating an instance to configure the behaviour of the instance (ie, batching event submissions).

## Contributing

Please feel free to contribute, pull requests very welcome. The aim is to build up this module to completely represent the API provided by Keen IO which quite extensive so the more contributions the better.

## Further Reading

Keen IO - Website: https://keen.io/

Keen IO - API Technical Reference: https://keen.io/docs/api/reference/

## Release History

### 0.0.1

- Add write/read keys.
- Reworked interface - not backwards compatible with 0.0.0!

### 0.0.0

- First release.

## License

Licensed under the MIT license.
