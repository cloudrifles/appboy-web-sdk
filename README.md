![Appboy Logo](https://github.com/Appboy/appboy-web-sdk/blob/master/Appboy_Logo_400x100.png)

# Web SDK

Effective marketing automation is an essential part of successfully scaling and managing your business. Appboy empowers you to build better customer relationships through a seamless, multi-channel approach that addresses all aspects of the user life cycle Appboy helps you engage your users on an ongoing basis. Visit the following link for details and we'll have you up and running in no time!

- [Read the full technical documentation](https://js.appboycdn.com/web-sdk/1.6/doc/module-appboy.html)

## Getting Started

To integrate the Appboy Web SDK, put the following snippet inside the `<head>` section of your page to load it dynamically:

<!--- UPDATE THESE LOADING SNIPPETS IN THE SAMPLE BUILD APP'S INDEX.HTML WHEN YOU CHANGE THEM!!
  For context, these are largely standard "load js from js" snippets - the basic approach is to create a script
  element, place it in the DOM, and the browser will do the remote fetch from the CDN. They're a little weird to
  read because they're semi-minimized to help reduce the amount of space we take up in peoples' applications.
  specifically, all the arguments to the snippet other than the onload callback (y) are only even params to reduce
  repetition and minimize snippet size. The cheekiness in the parameter naming was straight-up stolen from
  Localytics' version of this snippet: http://docs.localytics.com/#Dev/Integrate/web-integration.html

  Note that

  if (y.addEventListener) {
    y.addEventListener("load", b, false);
  }
  else if (y.readyState) {
    y.onreadystatechange = b;
  }

  is IE8 support: https://msdn.microsoft.com/en-us/library/hh180173(v=vs.85).aspx - when we drop IE8 we can strip this
  conditional out and just use the load listener.

  The INTERFACE_STUBBING_SNIPPET block is programmatically generated and templated by the grunt build from interface.json,
  using generate-interface-stub.js - to see the fully templated version, `grunt`, `grunt prepare-deployment`, and look
  inside build/public-docs/README.md
--->

```
<link rel="stylesheet" href="https://js.appboycdn.com/web-sdk/1.6/appboy.min.css" />
<script type="text/javascript">
  +function(a,p,P,b,y) {
    appboy={};for(var s="destroy toggleAppboyLogging setLogger openSession changeUser requestImmediateDataFlush requestFeedRefresh subscribeToFeedUpdates logCardImpressions logCardClick logFeedDisplayed requestInAppMessageRefresh logInAppMessageImpression logInAppMessageClick logInAppMessageButtonClick subscribeToNewInAppMessages removeSubscription removeAllSubscriptions logCustomEvent logPurchase isPushSupported isPushBlocked isPushGranted isPushPermissionGranted registerAppboyPushMessages unregisterAppboyPushMessages submitFeedback ab ab.User ab.User.Genders ab.User.NotificationSubscriptionTypes ab.User.prototype.getUserId ab.User.prototype.setFirstName ab.User.prototype.setLastName ab.User.prototype.setEmail ab.User.prototype.setGender ab.User.prototype.setDateOfBirth ab.User.prototype.setCountry ab.User.prototype.setHomeCity ab.User.prototype.setEmailNotificationSubscriptionType ab.User.prototype.setPushNotificationSubscriptionType ab.User.prototype.setPhoneNumber ab.User.prototype.setAvatarImageUrl ab.User.prototype.setLastKnownLocation ab.User.prototype.setUserAttribute ab.User.prototype.setCustomUserAttribute ab.User.prototype.addToCustomAttributeArray ab.User.prototype.removeFromCustomAttributeArray ab.User.prototype.incrementCustomUserAttribute ab.InAppMessage ab.InAppMessage.SlideFrom ab.InAppMessage.ClickAction ab.InAppMessage.DismissType ab.InAppMessage.OpenTarget ab.InAppMessage.ImageStyle ab.InAppMessage.Orientation ab.InAppMessage.CropType ab.InAppMessage.prototype.subscribeToClickedEvent ab.InAppMessage.prototype.subscribeToDismissedEvent ab.InAppMessage.prototype.removeSubscription ab.InAppMessage.prototype.removeAllSubscriptions ab.InAppMessage.Button ab.InAppMessage.Button.prototype.subscribeToClickedEvent ab.InAppMessage.Button.prototype.removeSubscription ab.InAppMessage.Button.prototype.removeAllSubscriptions ab.SlideUpMessage ab.ModalMessage ab.FullScreenMessage ab.ControlMessage ab.Feed ab.Feed.prototype.getUnreadCardCount ab.Card ab.ClassicCard ab.CaptionedImage ab.Banner ab.WindowUtils display display.automaticallyShowNewInAppMessages display.showInAppMessage display.showFeed display.destroyFeed display.toggleFeed sharedLib".split(" "),i=0;i<s.length;i++){for(var k=appboy,l=s[i].split("."),j=0;j<l.length-1;j++)k=k[l[j]];k[l[j]]=function(){console&&console.error("The Appboy SDK has not yet been loaded.")}}appboy.initialize=function(){console&&console.error("Appboy cannot be loaded - this is usually due to strict corporate firewalls or ad blockers.")};appboy.getUser=function(){return new appboy.ab.User};appboy.getCachedFeed=function(){return new appboy.ab.Feed};
    (y = a.createElement(p)).type = 'text/javascript';
    y.src = 'https://js.appboycdn.com/web-sdk/1.6/appboy.min.js';
    (c = a.getElementsByTagName(p)[0]).parentNode.insertBefore(y, c);
    if (y.addEventListener) {
      y.addEventListener("load", b, false);
    } else if (y.readyState) {
      y.onreadystatechange = b;
    }
  }(document, 'script', 'link', function() {
    appboy.initialize('YOUR-API-KEY-HERE');
    appboy.display.automaticallyShowNewInAppMessages();

    /*
     * If you have a unique identifier for this user (e.g. they are logged into your site) it's a good idea to call
     * changeUser here.
     * See https://js.appboycdn.com/web-sdk/latest/doc/module-appboy.html#.changeUser for more information.
     */
    // appboy.changeUser(userIdentifier);

    appboy.openSession();
  });
</script>
```

**Be sure to replace "YOUR-API-KEY-HERE" with your API key!** This snippet will provide a global variable named appboy that you can use to send data to the Appboy API.

----------------------------------------

Alternatively, you can use RequireJS or another AMD module-loader to load the Appboy Web SDK. In this scenario, we recommend hosting a copy of https://js.appboycdn.com/web-sdk/1.6/appboy.min.js alongside your other self-hosted Javascript resources, or utilizing your module-loader's packaging/optimization features to package the Appboy library inside of your other Javascript. This prevents the require call from failing when the library is blocked by strict corporate firewalls or ad blockers. If you opt for this route, please be sure to watch our Github repository at https://github.com/Appboy/appboy-web-sdk/releases in order to stay aware of critical bugfixes, releases, or other upgrades.

```
require(['appboy'], function(appboyModule) {
  appboyModule.initialize('YOUR-API-KEY-HERE');
  appboyModule.display.automaticallyShowNewInAppMessages();
  appboyModule.openSession();
});
```

**Be sure to replace "YOUR-API-KEY-HERE" with your API key!** Note that you'll still need to load the [css](https://js.appboycdn.com/web-sdk/1.6/appboy.min.css) (ideally self-hosted alongside the Javascript) in the `<head>` section of your page.

----------------------------------------

If your site uses npm to manage its client-side javascript, we also publish the Web SDK as an npm package, available [here](https://www.npmjs.com/package/appboy-web-sdk). To install it, use

```
$ npm install --save-dev appboy-web-sdk
```

This will install the Web SDK files into `./node_modules/appboy-web-sdk/appboy.min.js`/`./node_modules/appboy-web-sdk/appboy.min.css` where you can reference them locally. Note that the Appboy Web SDK is meant to be used client-side in a web application and will not work if required into a Node.js server.

----------------------------------------

If you don't intend to use Appboy's built-in UI capabilities (appboy.display), you can load a core version of the
library with display capabilities stripped. However, you will need to implement your own UI for In-App Messaging, the
News Feed, and Feedback. Note that our UI elements are fully customizable via css, so we generally recommend integration
of the complete library instead. The core library is available at `https://js.appboycdn.com/web-sdk/1.6/appboy.core.min.js`.

## Debugging / Troubleshooting

Pass the option `enableLogging: true` to your initialize function (`appboy.initialize('YOUR-API-KEY-HERE', {enableLogging: true});`) to cause Appboy to log to the javascript console. This is valuable for development but is visible to all users,
so remove this option or provide an alternate logger with {@link module:appboy.setLogger appboy.setLogger()} before you
release your page to production.

## Version Support

The Web SDK is a standards-compliant Javascript library, and is built to support a wide array of browser environments. That said, there are a few older browsers which are known to cause errors. For the following browsers, please observe the following version support restrictions:

- Internet Explorer > 8
- Opera > 11
- Android Browser > 2.3

Appboy uses [Font Awesome](http://fortawesome.github.io/Font-Awesome/) 4.3.0 for in-app message icons. Check out the [cheat sheet](http://fortawesome.github.io/Font-Awesome/cheatsheet/) to browse available icons.

## [Changelog](https://github.com/Appboy/appboy-web-sdk/blob/master/CHANGELOG.md)

## Questions?

If you have questions, please contact [support@appboy.com](mailto:support@appboy.com). If you believe you are encountering a bug, feel free to file issues in this repository.
