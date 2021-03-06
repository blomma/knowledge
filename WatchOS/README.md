# Independent Watch App and HealthKit

In the development of my latest app which is an Independent Watch App that uses HealthKit, I ran into an issue with App Store Connect. App Store Connect will complain about missing Purpose Strings, that is the messages display to the user when access permission is asked for health information.

> ITMS-90683: Missing Purpose String in Info.plist – Your app’s code references one or more APIs that access sensitive user data. The app’s Info.plist file should contain a NSHealthShareUsageDescription key with a user-facing purpose string explaining clearly and completely why your app needs the data. Starting Spring 2019, all apps submitted to the App Store that access user data are required to include a purpose string. If you’re using external libraries or SDKs, they may reference APIs that require a purpose string. While your app might not use these APIs, a purpose string is still required. You can contact the developer of the library or SDK and request they release a version of their code that doesn’t contain the APIs. Learn more (https://developer.apple.com/documentation/uikit/core_app/protecting_the_user_s_privacy).

> ITMS-90683: Missing Purpose String in Info.plist – Your app’s code references one or more APIs that access sensitive user data. The app’s Info.plist file should contain a NSHealthUpdateUsageDescription key with a user-facing purpose string explaining clearly and completely why your app needs the data. Starting Spring 2019, all apps submitted to the App Store that access user data are required to include a purpose string. If you’re using external libraries or SDKs, they may reference APIs that require a purpose string. While your app might not use these APIs, a purpose string is still required. You can contact the developer of the library or SDK and request they release a version of their code that doesn’t contain the APIs. Learn more (https://developer.apple.com/documentation/uikit/core_app/protecting_the_user_s_privacy).

This is regardless of whether the Property List in the Watch App Extension includes these properties.

## The Resolution

To resolve this issue, create a new Property List with no target set in your project at the root:

Inside that Property List add (or copy) the required HealthKit Property Strings to your new Property List file.

In short, these properties should be the only required properties in your file. Lastly, set this Property List file as the property list file of your app container target:

-   Click on the Project File in the Navigator on the right.
-   Select the App Container target.
-   This should be obvious since the target does not come with a Property List file on initial creation in Xcode.
-   Go to the Build Setting tab on the top.
-   Search for Info.plist File
-   In the field value enter the name of the newly created Info.plist file with your HealthKit Privacy strings set.

Now go ahead and archive and distribute your app to App Store Connect from the organizer as usual. App Store should be happy moving forward.
