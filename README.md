# react-native-esptouch-2

# I forked this repo to edit package react-native-esptouch-2 created by https://www.npmjs.com/package/@lorenzovecchi/react-native-esptouch-2/v/0.1.4      

Used to configure ESP devices to connect to target AP

- Support both Android and iOS
- iOS code is untested

This is a Unofficial project. The official demo is below:

[EsptouchForAndroid](https://github.com/EspressifApp/EsptouchForAndroid)

[EsptouchForIOS](https://github.com/EspressifApp/EsptouchForIOS)

## Installation

Install the module from npm

```sh
npm install @lorenzovecchi/react-native-esptouch-2
```

### Android

Add permissions in AndroidManifest.xml

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.CHANGE_WIFI_MULTICAST_STATE" />
```

### iOS

```sh
cd ios && pod install
```

## Usage

```js
import * as ESPTouch2 from "react-native-esptouch-2";

/**
* Start the configuration broadcasting the informations to the device
* @param {string} ssid
*   AP SSID
* @param {string} bssid
*   AP BSSID
* @param {string} password
*   AP Password (null if open network)
* @param {string} customData
*   Additional data to send (nullable)
* @param {string} aesKey
*   Encrypt the data to send (if not null, it must be 16 byte) (nullable)
*
* @resolve {object} res
*   Object containing the successfully configured device address and bssid
* @reject {Exception} err
*   Error exception
*/
ESPTouch2.start(ssid, bssid, password, customData, aesKey).then(res => {
    //On success
    console.log(res.address, res.bssid);
}).catch(err => {
    //On error
    console.log(err);
});

/**
* Stop the configuration broadcasting
*/
ESPTouch2.stop();

/**
* Function called on broadcasting start
*/
ESPTouch2.onStart(() => {console.log('Starting broadcast')};

/**
* Function called on broadcasting stop
*/
ESPTouch2.onStop(() => {console.log('Stopping broadcast')};
```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
