# SnapEngage Mobile SDK for Android

Install the SDK using Gradle Package manager, by copying the following line into the app module’s build.gradle file:

implementation "com.chat:sdk:0.4" // TBD

** Use the following until final release **

 implementation project(path: ':library')

 Instantiate a ChatView from code or layout XML file

 Kotlin:
```
 val chatView = ChatView(context)
```
 Java:

```
 ChatView chatView = new ChatView(context, null);
```

Import the SnapEngageSDK to your swift file:

```
import SnapEngageSDK
```

Instantiate a ChatView from code or StoryBoard:
```
let SnapEngageChat = ChatView()
```
Configure the ChatView
Create a Chat.Configuration object with your parameters. The constructor supports an optional parameter called customVariables.

Kotlin:
```
val provider = "SnapEngage"
// jsUrl from your SnapEngage code snippet
val jsUrl = "https://storage.googleapis.com/code.snapengage.com/js/your-widget-id.js"
val entryPageUrl = "https://yourdomain.com/"
val customVariables = CustomVariables()
	.put("accountNumber", 123456)
   	.put("customerSince", "December 1, 2016")
val config = Chat.Configuration(
provider, jsUrl, entryPageUrl, customVariables)
```

Java:
```
String provider = "SnapEngage";
// jsUrl from your SnapEngage code snippet
String jsUrl = "https://storage.googleapis.com/code.snapengage.com/js/your-widget-id.js";
String entryPageUrl = "https://yourdomain.com/";
CustomVariables customVariables = CustomVariables()
	.put("accountNumber", 123456)
	.put("customerSince", "December 1, 2016");
Chat.Configuration config = new Chat.Configuration(
provider, jsUrl, entryPageUrl, customVariables);
```

Setup the chatView with the configuration:
```
chatView.setConfiguration(config)
```
Register callbacks
You can observe several events of the SnapEngage chat by adding a listener to your chatView. You can add several listeners to the same event.
for example:

Kotlin:
```
val closeListener = object : CloseEventListener {
   override fun onClose(type: String?, status: String?) {
	Log.d("ChatView", "onCloseEvent triggered")
   }
})
chatView.addCloseListener(closeListener)
```
Java:
```
CloseEventListener closeListener = new CloseEventListener() {
   @Override
   public void onClose(
@Nullable String type,
@Nullable String status) {
       Log.d("ChatView", "onCloseEvent triggered");
   }
});
chatView.addCloseListener(closeListener);
```
You can also remove a listener:

Kotlin:
```
chatView.removeCloseListener(closeListener)
```
Java:
```
chatView.removeCloseListener(closeListener);
```
