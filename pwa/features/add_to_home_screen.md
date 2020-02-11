# Add PWA on Home Screen

To add web-app at home screen we have [web app manifest specifications][1], which specifies the standard way to implement this functionality.

## Browser Supports

See the latest browser support at [caniuse.com][2].

## Implementations

A complete `manifest.json` file for a progressive web app.

```json
{
  "short_name": "Maps",
  "name": "Google Maps",
  "icons": [
    {
      "src": "/images/icons-192.png",
      "type": "image/png",
      "sizes": "192x192"
    },
    {
      "src": "/images/icons-512.png",
      "type": "image/png",
      "sizes": "512x512"
    }
  ],
  "start_url": "/maps/?source=pwa",
  "background_color": "#3367D6",
  "display": "standalone",
  "scope": "/maps/",
  "theme_color": "#3367D6"
}
```

Add a link to specify your `manifest.json`.

```html
<link rel="manifest" href="/manifest.json" />
```

## Manifest Events

There are two events available while implementing app download.

```javascript
window.addEventListener("appinstalled", evt => {
  console.log("The app was installed.");
});
```

```javascript
window.addEventListener("beforeinstallprompt", evt => {
  evt.userChoice.then(choice => {
    var message =
      choice.outcome === "dismissed" ? "User cancelled" : "User Installed";

    console.log(message);
  });
});
```

Another approach can be implemented with this to show popup when user like to be in the app.

```javascript
window.addEventListener("beforeinstallprompt", evt => {
  evt.preventDefault();

  // save the event for later
  promptEvt = evt;

  return false;
});

if (promptEvt != undefined) {
  // show installed banner now

  promptEvt.prompt();

  promptEvt.userChoice.then(choice => {
    console.log("User Choice: ", choice.outcome);
  });
}
```

## Manifest Requirements

- You must provide **short_name and/or name** where `short_name` is used on the user's home screen, launcher, or other places where space may be limited. `name` is used in the app install prompt.

- `icons` should be provided where each object should include the `src`, a `sizes` property, and the `type` of image.

- `start_url` should direct the user straight into your app, rather than a product landing page. Think about what the user will want to do once they open your app, and place them there.

- `background_color` property is used on the splash screen when the application is first launched.

- `display`, you can customize what browser UI is shown when your app is launched. For example, you can hide the address bar and browser chrome. Or games may want to go completely full screen.

| Parameters |                                                                                                                                                                                                                                    |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| value      | Description                                                                                                                                                                                                                        |
| fullscreen | Opens the web application without any browser UI and takes up the entirety of the available display area.                                                                                                                          |
| standalone | Opens the web app to look and feel like a standalone native app. The app runs in its window, separate from the browser, and hides standard browser UI elements like the URL bar, etc.                                              |
| minimal-ui | This mode is similar to fullscreen, but provides the user with some means to access a minimal set of UI elements for controlling navigation (i.e., back, forward, reload, etc). <br> **Note**: Only supported by Chrome on mobile. |
| browser    | A standard browser experience.                                                                                                                                                                                                     |

- `orientation` You can enforce a specific orientation, which is advantageous for apps that work in only one orientation, such as games. Use this selectively. Users prefer selecting the orientation. Expected values `any`, `portrait-primary`, `landscape`.

- `scope` defines the set of URLs that the browser considers to be within your app, and is used to decide when the user has left the app. The `scope` controls the URL structure that encompasses all the entry and exit points in your web app. Your `start_url` must reside within the `scope`.
  <br> To learn more about the scope and other miscellaneous follow this [link][3].

> There are other manifest properties which you can have a look at.
> <br>https://www.w3.org/TR/appmanifest/

Application based properties are:

```json
{
  "screenshots": [
    {
      "src": "/path.ext"
    }
  ],
  "related_applications": [
    {
      "plateform": "play",
      "url": "http://url/to/app",
      "id": "com.example.app"
    }
  ],
  "prefer_related_applications": true
}
```

## Resources

To generate manifest [`realfavicongenerator`][4] will help you to create manifest online and generate all the icons that you will need for different platforms.

Use `chrome://inspect/#devices` for port forwarding when you are viewing your web app on the android emulator.

<!-- Link and Refs -->

[1]: https://developers.google.com/web/fundamentals/web-app-manifest
[2]: https://caniuse.com/#feat=web-app-manifest
[3]: https://developers.google.com/web/fundamentals/web-app-manifest#scope
[4]: https://realfavicongenerator.net/
