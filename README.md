# openhab_postman_templates
Postman Collections Templates for openHAB and openHAB Cloud for accessing the REST API.

Postman is an API platform for developers to design, build, test and iterate their APIs. As of April 2022, Postman reports having more than 20 million registered users and 75,000 open APIs, which it says constitutes the world's largest public API hub. The company is headquartered in San Francisco and maintains an office in Bangalore, where it was founded.

Postman can be used with Mac, Windows, & Linux. You can download it [here](https://www.postman.com/downloads/).

## Usage

### Local openHAB Instance

#### HTTP

If you want to connect to openHAB locally and with the `http` protocol you have to import `openhab-http.json`. Before importing please make sure that you change `<username>` to the username of your openHAB user. Also you have to change `<password>` to the password of your openHAB user. Of course you must also change `<your-ip>` to the ip address on which your openHAB instance is running. And at least you have to change `XXX` and `YYY`. This are parts of your ip address `192.168.XXX.YYY`.

It is recommended to use a text editor with a replace all function.

For testing you can install the [openhab_static_examples](https://github.com/Michdo93/openhab_static_examples). For this you can import `openhab-static-examples-http.json`. You have to make the same changes as described above.

#### HTTPS

If you want to connect to openHAB locally and with the `https` protocol you have to import `openhab-https.json`. Before importing please make sure that you change `<username>` to the username of your openHAB user. Also you have to change `<password>` to the password of your openHAB user. Of course you must also change `<your-ip>` to the ip address on which your openHAB instance is running. And at least you have to change `XXX` and `YYY`. This are parts of your ip address `192.168.XXX.YYY`.

It is recommended to use a text editor with a replace all function.

For testing you can install the [openhab_static_examples](https://github.com/Michdo93/openhab_static_examples). For this you can import `openhab-static-examples-https.json`. You have to make the same changes as described above.

### openHAB Cloud (as example myopenhab.org)

If you want to connect to openHAB remotely and use [myopenhab.org](https://myopenhab.org) you have to import `myopenhab.org.json`. Before importing please make sure that you change `<e-mail>` to the email address of your myopenhab.org user. Also you have to change `<password>` to the password of your myopenhab.org user.

It is recommended to use a text editor with a replace all function.

For testing you can install the [openhab_static_examples](https://github.com/Michdo93/openhab_static_examples). For this you can import `myopenhab.org-static-examples.json`. You have to make the same changes as described above.

## Additional notes

### Notes on HTTP request methods

As you can see with `openhab-static-examples-http.json`, `openhab-static-examples-https.json` or `myopenhab.org-static-examples.json` by testing the [openhab_static_examples](https://github.com/Michdo93/openhab_static_examples), you have to use `GET` to get the current `state` of an item, `PUT` for `postUpdate` an item and `POST` for `sendCommand` to an item.

| HTTP request method        | Description  | Method | URL  |
| :-------------: |:-------------:| :-----:| :-----:|
| `GET`  | Retrieve the state of an item. | `n/a` | `https://<base_url>/rest/items/{itemName}/state` |
| `PUT`  | The state of an item is updated. | `postUpdate` | `https://<base_url>/rest/items/{itemName}/state` |
| `POST` | A command is sent to an item via a channel. | `sendCommand` | `https://<base_url>/rest/items/{itemName}` |

The `<base_url>` could be the ip address plus port of your local openHAB instance (`<ip_address>:<port>`) or `myopenhab.org`. Of course if you are using `http` on your local instance you have to replace `https` with `http`.

### Notes on Event Bus Item Events

Of course you can try also to check the event of your item. Read more about it [here](https://www.openhab.org/docs/developer/utils/events.html#item-events). Sadly it will fail because [SSE](https://en.wikipedia.org/wiki/Server-sent_events) is not supported.
 
| HTTP request method |  Event | 	Description | 	URL | 
| :-------------: |:-------------:| :-----:| :-----:|
| `GET`  | ItemAddedEvent |	An item has been added to the item registry. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/added |
| `GET`  | ItemRemovedEvent |	An item has been removed from the item registry. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/removed |
| `GET`  | ItemUpdatedEvent |	An item has been updated in the item registry. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/updated |
| `GET`  | ItemCommandEvent |	A command is sent to an item via a channel. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/command |
| `GET`  | ItemStateEvent |	The state of an item is updated. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/state |
| `GET`  | ItemStatePredictedEvent |	The state of an item predicted to be updated. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/statepredicted |
| `GET`  | ItemStateChangedEvent |	The state of an item has changed. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/statechanged |
| `GET`  | GroupItemStateChangedEvent |	The state of a group item has changed through a member. |	https://<base_url>/rest/events?topics=openhab/items/{itemName}/{memberName}/statechanged |

The `<base_url>` could be the ip address plus port of your local openHAB instance (`<ip_address>:<port>`) or `myopenhab.org`. Of course if you are using `http` on your local instance you have to replace `https` with `http`.

As an alternative to Postman, you can then use curl for this:

|  Event | 	Description | 	URL | 
|:-------------:| :-----:| :-----:|
| ItemAddedEvent |	An item has been added to the item registry. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/added" |
| ItemRemovedEvent |	An item has been removed from the item registry. | curl	"https://<base_url>/rest/events?topics=openhab/items/{itemName}/removed" |
| ItemUpdatedEvent |	An item has been updated in the item registry. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/updated" |
| ItemCommandEvent |	A command is sent to an item via a channel. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/command" |
| ItemStateEvent |	The state of an item is updated. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/state" |
| ItemStatePredictedEvent |	The state of an item predicted to be updated. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/statepredicted" |
| ItemStateChangedEvent |	The state of an item has changed. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/statechanged" |
| GroupItemStateChangedEvent |	The state of a group item has changed through a member. |	curl "https://<base_url>/rest/events?topics=openhab/items/{itemName}/{memberName}/statechanged" |

### Notes on Creating a new Item via the REST API

You can create a new Item like described in the following:

| HTTP request method |  Event | 	Description | 	URL | 
| :-------------: |:-------------:| :-----:| :-----:|
| `PUT`  | Create a new item |	Creating a new item and add it to the item registry. |	`https://<base_url>/rest/items/{itemName}` |

In the `body` you have to use `JSON`. An equvialent command with `curl` looks like in the following:

```
curl -0 -v -X PUT http://<base_url>/rest/items/{itemName} -H "Content-Type: text/plain" -H 'Accept: text/plain' --data-binary @- << EOF
{
    "type": "String"
    "name": "myTestString",
    "label": "my test string"
}
EOF
```

In `Postman` you have to make sure to selecht `raw` and `JSON` inside the `Body` tag. There you can add:

```
{"type": "String", "name": "myTestString", "label": "my test string"}
```

The value will be `NULL`. If you want to add a value you can do something like in the following:

```
{"type": "String", "name": "myTestString", "label": "my test string", "value": "Hello World"}
```

If you want to add your item to a `Group` you have to do something like in the following:

```
{"type": "String", "name": "myTestString", "label": "my test string", "value": "Hello World", "groupNames": ["yourGroup"]}
```

If the `Group` to which you want to add the `Item` does not exist, you must first create this group:

```
{"type": "Group", "name": "yourGroup", "label": "my new own group"}
```

If you want this `Group` to be subordinate to another `Group`, you can do the following:


```
{"type": "Group", "name": "yourGroup", "label": "my new own group", "groupNames": ["parentGroup"]}
```

If this `Group` does not exist either, you can create this `Group` as described above.

You can also add an `Item` to multiple `Groups`. To do this, you need to do the following:

```
{"type": "String", "name": "myTestString", "label": "my test string", "value": "Hello World", "groupNames": ["firstGroup","secondGroup","thirdGroup"]}
```


### Notes on Deleting an Item via the REST API

You can delete an Item like described in the following:

| HTTP request method |  Event | 	Description | 	URL | 
| :-------------: |:-------------:| :-----:| :-----:|
| `DELETE`  | Delete an item |	Deleting an item and remove it from the item registry. |	`https://<base_url>/rest/items/{itemName}` |

### Notes on CRUD methods of an Item

`CRUD` stands for `Create, Read, Update and Delete`. In `openHAB` you can update an `Item` by using `postUpdate` or `sendCommand`. If you are working on your local instance you can run all `CRUD` methods. If you are using the openHAB Cloud you are limited to use `Read` and `Update`. By using the openHAB Cloud `Create` and `Delete` are not allowed.

| CRUD method | HTTP request method        | Description  | Method | URL  |
| :-----:| :-------------: |:-------------:| :-----:| :-----:|
| `Create`  | `PUT`  |	Creating a new item and add it to the item registry. |	`n/a` | `https://<base_url>/rest/items/{itemName}` |
| `Read`  | `GET`  | Retrieve the state of an item. | `n/a` | `https://<base_url>/rest/items/{itemName}/state` |
| `Update`  | `PUT`  | The state of an item is updated. | `postUpdate` | `https://<base_url>/rest/items/{itemName}/state` |
| `Update`  | `POST` | A command is sent to an item via a channel. | `sendCommand` | `https://<base_url>/rest/items/{itemName}` |
| `Delete` | `DELETE` |	Deleting an item and remove it from the item registry. |	`n/a` | `https://<base_url>/rest/items/{itemName}` |
