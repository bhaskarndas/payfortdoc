## Integrate Android SDK

------

You can also enable Payment processing through your mobile app by integrating PayFORT payment gateway. This section helps you to integrate PayFORT Android SDK with your android project and develop a a payment system for  your mobile  application.



To process a transaction using the FORT Mobile SDK, create a Mobile SDK Token and proceed through the following sections. Please refer to the SDK Token section by visiting this [link](mobilesdk.md)

### About the PayFORT Android SDK

------

#### List of Supported Platforms

The FORT Mobile SDK supports all devices running Android 4.1.x (API level 16).
ICE CREAM SANDWICH or higher are supported.
This release supports Android Pie API 28.

#### Localization Support

The FORT Mobile SDK supports both English and Arabic languages.

#### Screen Orientation

Portrait is the only orientation supported within the FORT Mobile SDK.

#### Supported Payment Methods

Through the first version of the FORT Mobile SDK, the Merchant has the ability to process a **CREDIT CARD** transactions only.

#### Supported Payment Options

The supported credit card payment options are **VISA**, **MASTERCARD**, **American Express (AMEX)**, **MADA** and **MEEZA**.

## Android Integration Flow

------

Placeholder : Explain the Integration Flow with diagram.





### Setting up Development Environment

------

**Prerequisites**

------

You are required to download the FORT android sdk  from this [link](mobilesdk.md). You can select either [eclipse](https://www.eclipse.org/downloads/) or [android studio](https://developer.android.com/studio/?gclid=CjwKCAjw8J32BRBCEiwApQEKgYlsVaAaHQq3SOIcbmlQwO1NSLHwhaCGlX4cmdxT7Twz4NsaMh6gNhoCD2MQAvD_BwE&gclsrc=aw.ds) for your development setup. You are also required to have some knowledge of mobile app development. You are also required to generate SDK Token.



**IDE Configurations**

------

**To start using the FORT Mobile SDK, Please follow the steps:**

Placeholder: Provide the pic

1. [Download](https://docs.payfort.com/docs/mobile-sdk/build/lib/FORTSDKv1.5.zip) the SDK and extract the SDK.

2. The folder contains **Dependencies**, **Res** and **FORTSDKv1.5.aar-release**.

   Dependencies folder includes:

   - **Eclipse folder**:

     1. .jar files for the SDK dependencies.
     2. LINKS_README text file that contains a list for sources of the above jars and a
        			 list of required libraries to be added as dependencies as well (Manual configuration).

   - **AndroidStudio_gradle** text file  which adds the compile command for what your project does not include.

   - **Res folder**:

     1. Layout
     2. Layout-ar

   - **FORTSDKv1.5.aar-release**

      	


  <div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Please make sure to read our notes according to the IDE you are using whether it’s the Android Studio or Eclipse.</div>     

## Android Studio Project Setup

------

Once you have downloaded and extracted the PayFORT SDK as explained above you can next setup the Android Studio. To continue the integration, please proceed with the following steps:

1. Go to File → New → New Module.

Placeholder: Pictures of Android Studio for each step.

1. Select “Import .JAR/.AAR Package” and click next.
2. Enter the path to .aar file and click finish.
3. Browse to the dependencies folder and open the “AndroidStudio_gradle” text file.
4. Copy and paste the implementation/ api lines that are NOT already supported in your dependency block. (All listed dependencies are  required).
5. Click the “Sync the project with gradle files” button.
6. Clean the project.
7. The SDK is now ready for your use.

## Eclipse Project Setup

------

Incase you are using Eclipse instead of Android Studio then you can ignore the above section and follow the instructions in this section. The integration will include two main steps. For the first step, you need to create a library project by following the below steps:

1. Create a new project (from this time it’s called “library project”) in your workspace.

   Placeholder: Provide picture of Eclipse platform for each step.

2. Do not forget to mark it as library.

3. Clear the src folder of the library project.

4. Unzip the .aar file. You can rename it to zip and then unzip it or use any tool.

5. Copy the classes.jar file to libs folder on the library project.

6. Replace the res folder on library project with the res folder of the .aar file.

## Project Configuration

------

Once the IDEs have been installed, next we will configure the project. This section discusses the steps to configure the Project. The configuration will help to integrate the PayFORT android SDK with the IDE. 

The project you have created contains almost everything you need. Now let’s start configuring your project to reference this library project by following the below points:

Placeholder: Provide pictures for project configuration.

1. In the target project, use the library created in step one (mentioned above) as a dependency.
2. Open the AndroidManifest.xml file inside .aar file and make sure to copy everything it takes (permissions, activities, services, receivers …) in the AndroidManifest.xml file of the target project.
3. Copy the entire contents (if any) inside the assets folder of the .aar file to the assets folder of the target project.
4. Copy the entire contents (if any) inside the libs folder of the .aar file to the libs folder of the target project.
5. Open the dependencies file → Eclipse, then copy all .jar files and add them to the libs folder of the target project.
6. Check if your target project has the project dependencies included in the LINKS_README text file under the LINKS_README text file under the libraries (Projects/aar). Otherwise use the links included in the previously mentioned file and add them as a dependency project on your target project.
7. Clean and rebuild your target project.



## OS Permissions

------

The PayFORT android SDK requires the following android OS permissions to work properly as shown by the following code. You are required to include the below code in your project. 

```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.READ_PHONE_STATE"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```



## Using the FORT Mobile SDK

------

**Collect the FORT Mobile SDK Request Through a Java Bean**

You can create a Java bean class for the PayFORT Mobile SDK request as shown below:

```java
// FORT Mobile SDK request

public class FortRequest implements Serializable{
private Map<String, Object> requestMap;
private boolean showResponsePage;
public Map<String, Object> getRequestMap() {
   return requestMap;
}
public void setRequestMap(Map<String, Object> requestMap) {
  this.requestMap = requestMap;
}
public boolean isShowResponsePage() {
  return showResponsePage;
}
public void setShowResponsePage(boolean showResponsePage) {
  this.showResponsePage = showResponsePage;
}
}
```

The following are the Mobile SDK Call Parameters:

- The “requestMap” will contain all the PayFORT [parameters](androidsdkoperations.md) of the order/ transaction.
- “showResponsePage” is the Boolean field where you can determine if you want the FORT response page to be displayed or not. 

**Define a Callback Manager**

Define and initialize an instance of the **FortCallBackManager** in your activity as shown below:

```java
// FORT Callback Manager Instance

private FortCallBackManager fortCallback = null;
fortCallback = FortCallback.Factory.create();
```

**Attach the Callback to the Activity**

You need to add the statement that appears below to the **onActivityResult** function.

```java
//Callback Statement
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
super.onActivityResult(requestCode, resultCode, data);
fortCallback.onActivityResult(requestCode,resultCode,data);
}
```

**Call the FORT Mobile SDK**

For every transaction that needs to be processed, do the call as shown below and handle the callback methods upon your business flow. The FORT Mobile SDK Call registers a new callback for a new request. The **registerCallBack** requires the inputs as shown below.

```java
//FORT Mobile SDK Call
FortSdk.getInstance().registerCallback(this,fortRequest,5, fortCallback, showLoading, new FortInterfaces.OnTnxProcessed() {
@Override
public void onCancel(Map<String, Object> requestParamsMap,Map<String, Object> responseMap) {
        //TODO: handle me
    }
@Override
public void onSuccess(Map<String, Object> requestParamsMap, Map<String, Object> fortResponseMap) {
        //TODO: handle me
    }
@Override
public void onFailure(Map<String, Object> requestParamsMap, Map<String, Object> fortResponseMap) {
        //TODO: handle me
    }
@Override
public void onSuccess(Map<String, Object> requestParamsMap, Map<String, Object> fortResponseMap) {
       //TODO: handle me
}
});
```

**Register Callback Request**

```java
//The registerCallBack Request
  public void registerCallback(
  Activity context,
  final FortRequest fortRequest,
  String environment,
  final int requestCode,
  final FortCallBackManager callbackManager,
  boolean showLoading,
  final FortInterfaces.OnTnxProcessed callback)
```

**Call the Fort SDK Function**

```java
//FortSDK function
String device_id = FortSdk.getDeviceId(this);
```



**FORT Mobile SDK Device ID Value**

Please Make sure to use the FortSDK function[&nbsp;<i class="fa fa-anchor"></i>](#call-the-fort-sdk-function) as shown above to generate the device_id parameter value that must be used for creating the sdk_token from your business security server.

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>The Merchant can choose to display the FORT response page by passing “showResponsePage” value as “True”.</div>

## **Customizing the Mobile SDK Payment Layout**

------

We provide you with the res folder that includes the source code of the pages in order to customize the design, themes, etc. You can customize both English and Arabic layouts as needed. However, please take the following tips into consideration:



Placeholder: Provide Android UI flow diagrams and Android based mobile screenshots.

1. Don’t change the layout name because it’s considered an override process.
2. Make sure to use all the views that has the ID property in order to avoid the NullPointerException.
3. Redesign the view for portrait orientation. Note that Landscape orientation isn’t supported.
4. You can support as much layout densities as you want.
5. Don’t forget to redesign the layout-ar file too (right-to-left).
6. Don’t change, rename, or remove onClick functions.

 **Our Mobile SDK v 1.5 consists one of the following three main activities design:**

- activity_cc_payment.xml
- activity_cc_response.xml
- activity_init_secure_conn

Every file is available for both English and Arabic alignments; layout and layout-ar.

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>The files Hierarchy and Content might change in our SDK’s future versions.</div>

**Design Customization Codes:**

The following code was used to customize the way the “Amount” is displayed in the **Standard** Mobile SDK Payment Page:

```html
<TextView
android:id=“@+id/amountTV”
android:layout_width=“match_parent”
android:layout_height=“@dimen/pf_payment_type_header_height”
android:background=“@color/pf_light_gray”
android:gravity=“center_horizontal|center_vertical”
android:textColor=“@android:color/black”
android:textSize=“@dimen/pf_15_txt_size” />
```

The following code is used to customize the way the “Amount” is displayed in the **Customized** Mobile SDK Payment Page:

```xml
LinearLayout
android:layout_width=“match_parent”
android:layout_height=“wrap_content”
android:orientation=“horizontal”
android:padding=“10dp”
android:background=“@android:color/white”>

<ImageView
android:layout_width=“40dp”
android:layout_height=“40dp”
android:src=“@drawable/merchant_logo”/>

<TextView
android:fontFamily=“sans-serif-medium”
android:text=“Merchant name”
android:layout_margin=“10dp”
android:textColor=“@android:color/holo_blue_dark”
android:layout_width=“wrap_content”
android:layout_gravity=“center_vertical”
android:layout_height=“wrap_content”
android:src=“@drawable/merchant_logo”/>

<TextView
android:id=“@+id/amountTV”
android:layout_width=“match_parent”
android:layout_height=“@dimen/pf_payment_type_header_height”
android:gravity=“right|center_vertical”
android:textColor=“@android:color/black”
android:text=“100 UDS”
android:textSize=“@dimen/pf_15_txt_size” />

</LinearLayout>


```

- As appears in the previous codes, elements with IDs haven’t been changed in type or removed. For example: android:id=“@+id/amountTV”.

- We were able to add static elements such as: **ImageView** element that contains the Merchant’s logo, and **TextView** that contains the Merchant’s name.

- To sum up, you can add any static elements or redesign the view, while keeping the views’ elements used in the Standard layout that hold IDs.

  

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>Make sure to retest your custom design, for example, by showing the error messages on fields and applying the changes to the Arabic layout. (Refer to the points mentioned under the **Customizing the Mobile SDK Payment Layout** section).</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info">&nbsp;&nbsp;</i>The customized XML file should be added to the layout file in the target project (Merchant Application) to override the SDK file.</div>

## PayFORT Android SDK Operations

------

Once you have done the project setup and installation, you will be performing the Operations for authorization and purchase done through mobile application. These operations helps your mobile application to process Authorization and Purchase operations. You will be sending the request parameters in your code which will be sent to the PayFORT server and your application will receive response from the PayFORT server. 

**Sample Code**

```java
public class PayFortSdkSample extends Activity {

private FortCallBackManager fortCallback = null;
String deviceId = “”, sdkToken = “”;

@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

// create Fort callback instance
fortCallback = FortCallback.Factory.create();

// Generating deviceId
deviceId = FortSdk.getDeviceId(PayFortSdkSample.this);
Log.d(“DeviceId ”, deviceId);

// prepare payment request
FortRequest fortrequest = new FortRequest();
fortrequest.setRequestMap(collectRequestMap(“PASS_THE_GENERATED_SDK_TOKEN_
HERE”));
fortrequest.setShowResponsePage(true); // to [display/use] the SDK response page

// execute payment request
callSdk(fortrequest);
}

private Map<String, Object> collectRequestMap(String sdkToken) {
Map<String, Object> requestMap = new HashMap<>();
requestMap.put(“command”, “PURCHASE”);
requestMap.put(“customer_email”, “Sam@gmail.com”);
requestMap.put(“currency”, “SAR”);
requestMap.put(“amount”, “100”);
requestMap.put(“language”, “en”);
requestMap.put(“merchant_reference”, “ORD-0000007682”);
requestMap.put(“customer_name”, “Sam”);
requestMap.put(“customer_ip”, “172.150.16.10”);
requestMap.put(“payment_option”, “VISA”);
requestMap.put(“eci”, “ECOMMERCE”);
requestMap.put(“order_description”, “DESCRIPTION”);
requestMap.put(“sdk_token”, sdkToken);
return requestMap;
}

private void callSdk(FortRequest fortrequest) {

try {
FortSdk.getInstance().registerCallback(PayFortSdkSample.this, fortrequest, FortSdk.ENVIRONMENT.TEST, 5, fortCallback, new FortInterfaces.OnTnxProcessed() {
@Override
public void onCancel(Map<String, Object> requestParamsMap, Map<String,
Object> responseMap) {
//TODO: handle me
Log.d(“Cancelled ”, responseMap.toString());
}

@Override
public void onSuccess(Map<String, Object> requestParamsMap, Map<String,
Object> fortResponseMap) {
//TODO: handle me
Log.i(“Success ”, fortResponseMap.toString());
}

@Override
public void onFailure(Map<String, Object> requestParamsMap, Map<String,
Object> fortResponseMap) {
//TODO: handle me
Log.e(“Failure ”, fortResponseMap.toString());
}

});
} catch (Exception e) {
Log.e(“execute Payment”, “call FortSdk”, e);
}

}

@Override
public void onActivityResult(int requestCode, int resultCode, Intent data) {
super.onActivityResult(requestCode, resultCode, data);
fortCallback.onActivityResult(requestCode, resultCode, data);
}

```



Placeholder for sample response from the PayFORT server.

You can check out the request and response parameters by visiting this [link](androidsdkoperations.md).

### PayFORT Android SDK – Device ID permission

------

This section helps the developers to understand the need and usage of the permission requested by the PayFORT Payment SDK to generate a unique device ID.

<div class="alert alert-info"><i class="fa fa-info">&nbsp;&nbsp;</i>
    You might not face this issue through your payment flow. It depends on the time you are requesting the getDeviceID function and ask about the permission for the first time.
</div>

A part of the FORT mobile SDK flow is to get a unique ID for the device. Generating the ID based on more than one input (collecting as much as possible will lead to a real unique ID).

The Telephone manager is one of these sources. Accessing the Telephone manager need the use of ‘android.permission.READ_PHONE_STATE’ permission. According to Android that’s a dangerous permission to be used. Getting the needed permission through the flow on the case of getting the client granted that will produce a miss match device ID on the 1st SDK call.

To avoid the mismatch flow we are suggesting you the following solutions:

- **Handle the 1st SDK call in the onActivityResults().**
  Since The FORT SDK is a module running within the main application context the requested permission response will be returned to the merchant context. Once the activity that called geDeviceId for the 1st received a call-back in the onActivityResult() with request code = 222 you can for sure starts the payment flow of creating an SDK token and calling the SDK afterwards.

- Call getDeviceID on a previous activity or in your application class to make sure that the permission request was triggered before you reach the payment step.



## Go to Full API

------

Check out our full API by visiting this [link](https://docs.payfort.com/docs/api/build/index.html#redirection)

## Need further help?

------

Thanks for using PayFort.com. If you need any help or support, then message our support team at [support@payfort.com](mailto:support@payfort.com).

