# Progressive Web App

Let see how this concept of Progressive Web Apps came into existence. Previously with the launch of Web 1.0(in 1998), we can create webpages with images and texts. Which was improved around 2004 where we can load videos and audios using flash and Silverlight, which also helps us to animate UI and interact on events.

After the launch of Apple iPhone in 2007, Steev Jobs changed the world and introduces Apps. He was not fond of Flash or Silverlight. So he wants us to use simple web technologies to create apps for iPhones. After the launch of Android, everyone focussed on native mobile application development. Due to which they have to create multiple apps for different platforms.

To find the solution for reducing development time, in the year of 2016 Alex Russell named this technique of pure web app development with the functionality of notifications and using Service Worker for offline loading as Progressive Web App. To learn more about the history of app development follow this [link][1].

But before reading more about history, let's take a look at the attributes that define Progressive Web Apps(PWA).

## 9 Attributes of PWA's

1. **Responsive** - Your application will fit any form factor.
2. **Connectivity Independent** - Can work on both online and offline or even on the slow network.
3. **App Like Interface** - Your application should look and feel like Native App(Navigations and view should look like native app.)
4. **Fresh** - Your app should be daily updated and those updates are effected daily.
5. **Safe** - Your app should be safe as it should run on transport layer security. You must run your app on HTTPS connection.
6. **Discoverable** - Your web-app should be identified as an application using W3S manifestation. As well as the search engines can find them.
7. **Re-engageable** - The application should use operating system features to re-engage users, commonly known feature is Push Notification.
8. **Installable** - Allow users to add them to home screens.
9. **Linkable** - There should be no friction at all to getting into apps. A single URL should be the entry point to the application.

## Fundamentals

I'm going to cover the following fundamentals.

- [Going Offline][2]
- [Adding to Home Screen][3]
- [Sending Push Notifications][4]
- [Background Syncing][5]
- [Best Practices for PWAs][6]

## Install App Banner Requirements

- APP should run on HTTPS connection with Secure Green Icon.
- Has a Service Worker registered
- Must have the offline experience
- Web App Manifest with required properties.

<!-- Links and Refs -->

[1]: https://dzone.com/articles/journey-of-an-app-from-native-to-progressive
[2]: features/going_offline.md
[3]: features/add_to_home_screen.md
[4]: features/push_notifications.md
[5]: features/background_syncing.md
[6]: features/best_practices.md
