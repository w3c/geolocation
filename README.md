# Geolocation API

Welcome to the home of the W3C's Geolocation API!

Once a user grants permission, the Geolocation API provides access to geographical location information from device.

This repository is where the friendly folks of the [Devices and Sensors Working Group](https://www.w3.org/das/) maintain the specification.

- [Editor's draft](http://w3c.github.io/geolocation-api/)

## Examples of usage

This HTTPs-only API exposes the `navigator.geolocation` object with a couple of useful methods:

- `.getCurrentPosition(successCallback, [errorCallback, options])` - "one shot" position request
- `.watchPosition(successCallback, [errorCallback, options])` - Watch a position and get notified of any changes.
- `.clearWatch(someId)` - allows you to stop watching for location changes.

No location information is made available through this API without the user's permission.

### `navigator.geolocation.getCurrentPosition()` method

Request the user's current location. If the user allows it, you will get back a position object.

```JS
navigator.geolocation.getCurrentPosition(position => {
  const { latitude, longitude } = position.coords;
  // Do something cool with latitude, longitude
});
```

### `navigator.geolocation.watchPosition()` method

Request the ability to watch user's current location. If the user allows it, you will get back continuous updates of the user's position.

```JS
const watchId = navigator.geolocation.watchPosition(position => {
  const { latitude, longitude } = position.coords;
  // Do something cool with latitude, longitude
});
```

### `navigator.geolocation.clearWatch()` method

Finally, stop watching the user's location.

```JS
navigator.geolocation.clearWatch(watchId);
```

### More examples

The specification provides [examples](https://w3c.github.io/geolocation-api/#examples) covering different use case.
