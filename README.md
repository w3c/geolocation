# Geolocation

Once a user grants permission, Geolocation provides access to geographical location information from device.

- [Editor's draft](http://w3c.github.io/geolocation/)

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

### `GeolocationPosition` as JSON

You can also easily treat `GeolocationPosition` objects as JSON:

```JS
async function sendPosition() {
  try {
    // Get the current position
    const position = await new Promise((resolve, reject) => {
      navigator.geolocation.getCurrentPosition(resolve, reject);
    });

    // .stringify() calls .toJSON() automatically
    const body = JSON.stringify(position, null, 2);

    // Prepare the fetch request options
    const options = {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body
    };

    // Send request
    await fetch('https://example.com/api/positions', options);
  } catch (error) {
    console.error('Error getting or sending position data:', error);
  }
}

sendPosition();
```

### More examples

The specification provides [examples](https://w3c.github.io/geolocation/#examples) covering different use case.
