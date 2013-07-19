App42-Android-Push-Sample
==========================


# About Application

1. This application shows how can we integrate our application for PushNotification using App42 API.

# Running Sample

This is a sample Android app is made by using App42 backend platform. It uses Push Notification API of App42 platform.
Here are the few easy steps to run this sample app.

1. [Register] (https://apphq.shephertz.com/register) with App42 platform.
2. Create an app once you are on Quick start page after registration.
3. If you are already registered, login to [AppHQ] (http://apphq.shephertz.com) console and create an app from App Manager Tab.
4. To use push Notification service in your application go to https://code.google.com/apis/console a new project here.
5. Click on services option in Google console and enable Google Cloud Messaging for Android service.
6. Click on API Access tab and create a new server key for your application with blank server information.
7. Go to [AppHQ] (http://apphq.shephertz.com) console and click on Push Notification and select Android setting in Settings option.
8. Select your app and copy server key that is generated by using Google API console in step 6, and submit it.
9. Download the project from [here] (https://github.com/shephertz/App42-Android-Push-Sample/archive/master.zip) and import it in the eclipse.
10. Open MainActivty.java file in sample app and make following changes.

```
A. Replace api-Key and secret-Key that you have received in step 2 or 3 at line number 18 and 19.
C. Replace your user-id by which you want to register your application for PushNotification at line number 20.
B. Replace project-no with your Google Project Number at line number 21.
```
11.Build your android application and install on your android device.

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


__Customize PushNotification Message:__ You can customize your PushNotification message by changing following code in GCMIntentService.java file.
  
```
  Notification notification = new NotificationCompat.Builder(context)
        .setContentTitle(title)
        .setContentText(message)
        .setContentIntent(intent)
        .setSmallIcon(icon)
        .setWhen(when)
        .setLargeIcon(getBitmapFromURL(LARGE_IMAGE_URL))
        .setLights(Color.YELLOW, 1, 2)
        .setAutoCancel(true)
        .build();
        notificationManager.notify(0, notification);

```

__ Change Message Activty:__ You can novigate to desired Activty ,which you want to open when Notification is clicked. For thic you can replace MessageActivity with 
that Activty you want to navigate in AndroidManifest.xml file. 
  
```
     <meta-data android:name="onMessageOpen" android:value="com.example.app42sample.MessageActivity" />

```
