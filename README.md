App42-Android-Push-Library
==========================


# About Application

1. This application shows how can we integrate our application for PushNotification using App42 API.
2. We can use this sample as a library project for our android application.

# Running Sample

This is a sample Android gaming app is made by using App42 backend platform. It uses Push Notification of App42 platform.
Here are the few easy steps to run this sample app.

1. [Register] (https://apphq.shephertz.com/register) with App42 platform.
2. Create an app once you are on Quick start page after registration.
3. If you are already registered, login to [AppHQ] (http://apphq.shephertz.com) console and create an app from App Manager Tab.
4. [To use Push Notification see video] (http://www.youtube.com/watch?feature=player_embedded&v=4FtpoRkPuPo).
5. To use push Notification service in your application go to https://code.google.com/apis/console a new project here.
6. Click on services option in Google console and enable Google Cloud Messaging for Android service.
7. Click on API Access tab and create a new server key for your application with blank server information.
8. Go to [AppHQ] (http://apphq.shephertz.com) console and click on Push Notification and select Android setting in Settings option.
9. Select your app and copy server key that is generated by using Google API console, and submit it.
10. Download the eclipse project from this repo and import it in the same.
11. You can use this sample as a library project or can be used accordingly.
12. Open MainActivty.java file in sample app and make these changes.

```
A. Replace api-Key and secret-Key that you have received in step 2 or 3 at line number 18 and 19.
C. Replace your user-id by which you want to register your application for PushNotification at line number 20.
B. Replace project-no with your Google Project Number at line number 21.
```
13.Build your android application.

__Test and verify PushNotification__
  
```
A. After registering for PushNotification go to AppHQ console and click on Push Notification and select 
  application after selecting User tab.
B. Select desired user from registered UserList and click on Send Message Button.
C. Send appropriate message to user by clicking Send Button.

```

__Send Message using App42 API :__ If you want to send PushNotification using App42 API , pass the userId and 
message in below method .
  
```
PushNotificationService pushService=App42API.buildPushNotificationService();
pushService.sendPushMessageToUser(userId,message);

```

# Design Details:
__Intialization :__ You have to initialize  your application first before registering for PushNotification in your MainActivty.java file.

```
    App42API.initialize(
        this,
        "<YOUR API KEY>",
        "<YOUR SECRET KEY>");
     App42API.setLoggedInUser("YOUR USER ID") ;
    Util.registerWithApp42("<Your Google Project No>")
```
__PusHNotification Registration Steps :__
  
```
A. First we have to register our device on Google Cloud Messaging(GCM) using Google ProjectNo.
     
     GCMRegistrar.register(App42API.appContext, senderId);
     
B. After that when we get GCM registration id , we have to register on APP42 Platform.
 
  final String deviceRegId = GCMRegistrar.getRegistrationId(App42API.appContext);
  App42API.buildPushNotificationService().storeDeviceToken(App42API.getLoggedInUser(), deviceRegId, new App42CallBack() {

                            @Override
                            public void onSuccess(Object paramObject) {
                                // TODO Auto-generated method stub
                                App42Log.debug(" ..... Registeration Success ....");
    GCMRegistrar.setRegisteredOnServer(App42API.appContext, true);
                            }

                            @Override
                            public void onException(Exception paramException) {
                                App42Log.debug(" ..... Registeration Failed ....");
                                App42Log.debug("storeDeviceToken : Exception : on start up " +paramException);

                            }
                        });

```
