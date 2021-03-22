# Geolocation API

Welcome to the home of the W3C's Geolocation API!

The API that provides access to geographical location information from device.

This repository is where the friendly folks of the [Devices and Sensors Working Group](https://www.w3.org/das/) maintain the specification.

- [Editor's draft](http://w3c.github.io/geolocation-api/)

## Examples of usage

This HTTPs-only API exposes a namespace (`geolocation`) with a couple of useful methods:

- `.getCurrentPosition(successCallback, [errorCallback, options])` - "one shot" position request
- `.watchPosition(successCallback, [errorCallback, options])` - Watch a position and get notified of any changes.
- `.clearWatch()` - allows you to stop watching for location changes.

### .getCurrentPosition() method

Request the user's current location. If the user allows it, you will get back a position object.

```JS
navigator.geolocation.getCurrentPosition(position => {
  const { latitude, longitude } = position.coords;
  // Do something cool with latitude, longitude
});
```

### .watchPosition() method

Request the ability to watch user's current location. If the user allows it, you will get back continuos updates of the user's position.

```JS
const watchId = navigator.geolocation.watchPosition(position => {
  const { latitude, longitude } = position.coords;
  // Do something cool with latitude, longitude
});
```

### .clearWatch() method

Finally, stop watching the user's location.

```JS
navigator.geolocation.clearWatch(watchId);
```

### More examples

The specification provides a [great range of examples](https://w3c.github.io/geolocation-api/#examples) covering a diverse range of different use case.
