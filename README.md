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

## Notes on HTTP request methods

As you can see with `openhab-static-examples-http.json`, `openhab-static-examples-https.json` or `myopenhab.org-static-examples.json` by testing the [openhab_static_examples](https://github.com/Michdo93/openhab_static_examples), you have to use `GET` to get the current `state` of an item, `PUT` for `postUpdate` an item and `POST` for `sendCommand` to an item.

| HTTP request method        | Description  | URL  |
| :-------------: |:-------------:| :-----:|
| `GET`  | Retrieve the state of an item | `https://<base_url>/rest/items/{itemName}/state` |
| `PUT`  | The state of an item is updated. | `https://<base_url>/rest/items/{itemName}/state` |
| `POST` | A command is sent to an item via a channel. | `https://<base_url>/rest/items/{itemName}` |

The `<base_url>` could be the ip address plus port of your local openHAB instance (`<ip_address>:<port>`) or `myopenhab.org`.
