# _Argon SDK - Version 1.0_

---

_Description: Android library for Argon API_

## Argon SDK Setup

To start using the Argon SDK you first need to do: 

_Copy the **argonsdk.jar** to your project libs folder_

## Argon SDK initialization
_Steps needed to initialize the sdk_
####Setup Argon SDK credentials:
    public class YourApplication extends Application
    {
         ...
         @Override
         public void onCreate(){
             super.onCreate();
             ...
             ArgonSDK.setCredentials(this, YOUR_ARGON_ACCES_TOKKEN, YOUR_ARGON_CLIENT_ID, YOUR_ARGON_CLIENT_SECRET);
             ...
         }
    }

**In the project manifest:**

    ...
    <application
        android:name=".YourApplication"
    ...

## Running the API functions
_In your Activity/Fragment file run the following to types of AsyncRequest to access the API calls:_
### AsyncRequest:
_The AsyncRequest has the following constructors:_

- ``` AsyncRequest(Context context, IOnFinishWithDataCallback onResponse)```
# 
    IOnFinishWithDataCallback onResponse 
- this code will be runned on post execute, the following is needed to see if the request was succesfull or not:

Ex:

    new IOnFinishWithDataCallback() {
         @Override 
         public void onFinish(Object caller) {
		      ArgonUserResponse response = ((UserResponse) caller);
		      if (response != null && response.isOk()) {
			       if (response.getUser() != null) {
				   // 
			       }  
		      }
         }
 }

- ``` AsyncRequest(Context context, IOnFinishWithDataCallback onResponse, IOnPreExecuteCallback onPreExecute)```
# 
    IOnPreExecuteCallback onPreExecute
- this code will be runned in pre execute, this can be null if no code is needed to run in onPreExecute() section of the AsyncTask request;

## Argon API Calls

### 1. Register user:

Ex:

    new AsyncRequest(context, new IOnFinishWithDataCallback() {
         @Override 
         public void onFinish(Object caller) {
		      ArgonUserResponse response = ((UserResponse) caller);
		      if (response != null && response.isOk()) { //response.isOk() - returns if the request was done succesfully or not
                   //response.save(context) - Call this if you want to save an instance to memory of the UserResponse, You can use this UserResponse instance to get the ArgonUser fields.
			       if (response.getUser() != null) { //response.getUser() - returns an ArgonUser Object;
				   // Do something with the user
			       }  
		      } else {
                  //Fail block
              }
         }
    }).execute(argonUser);

_argonUser - an instance of the ArgonUser Object class - in this object you can set the register parameters of the user. **argonUser apiMethod needs to be set to CallMethod.POST to access the Register function.**_


### 2. Login user:

Ex:

    new AsyncRequest(LoginActivity.this, new IOnFinishWithDataCallback() {
	     @Override
	     public void onFinish(Object caller) {
		     ArgonUserResponse = ((UserResponse) caller);
		     if (response != null && response.isOk()) {
                //response.save(context) - Call this if you want to save an instance to memory of the UserResponse, You can use this UserResponse instance to get the ArgonUser fields.
                ...
             } else { //Fail block }
        }
    }).execute(basicUserFields);

_basicUserFields - and Instance of BasicUserFields, this Object has screenname and password fields needed to login._ _Login request returns an ArgonUserResponse object._

### 3. Get user:
Ex:

    new AsyncRequest(context, new IOnFinishWithDataCallback() {
         @Override 
         public void onFinish(Object caller) {
		      ArgonUserResponse response = ((UserResponse) caller);
		      if (response != null && response.isOk()) { //response.isOk() - returns if the request was done succesfully or not
                   //response.save(context) - Call this if you want to save an instance to memory of the UserResponse, You can use this UserResponse instance to get the ArgonUser fields.
			       if (response.getUser() != null) { //response.getUser() - returns an ArgonUser Object;
				   // Do something with the user
			       }  
		      } else {
                  //Fail block
              }
         }
    }).execute(argonUser);

_argonUser - an instance of the ArgonUser Object class - in this object you can set the register parameters of the user. **argonUser apiMethod needs to be set to CallMethod.GET to access the GetUser function. (  argonUser.setApiMethod(CallMethid.GET) )**_

### 4. Update user:
Ex:

    new AsyncRequest(context, new IOnFinishWithDataCallback() {
         @Override 
         public void onFinish(Object caller) {
		      ArgonUserResponse response = ((UserResponse) caller);
		      if (response != null && response.isOk()) { //response.isOk() - returns if the request was done succesfully or not
                   //response.save(context) - Call this if you want to save an instance to memory of the UserResponse, You can use this UserResponse instance to get the ArgonUser fields.
			       if (response.getUser() != null) { //response.getUser() - returns an ArgonUser Object;
				   // Do something with the user
			       }  
		      } else {
                  //Fail block
              }
         }
    }).execute(argonUser);

_argonUser - an instance of the ArgonUser Object class - in this object you can set the register parameters of the user. **argonUser apiMethod needs to be set to CallMethod.PUT to access the GetUser function. (  argonUser.setApiMethod(CallMethid.PUT) )**_

### 5. Screen name suggestions:
Ex:

    new AsyncRequest(context, new IOnFinishWithDataCallback() {
		@Override
		public void onFinish(Object caller) {
			ScreenNameSuggestion response = ((ScreenNameSuggestion) caller);
			if (response != null && response.isOk()) {
                 response.getAvailableScreenNames() // returns a string with a list of suggestions
			} 
		}
	}).execute(new ScreenNameSuggestion(screenName));

_screenName - the username that the user wants to use._

### 6. Screen name availability:
_Checks if the user is available_

Ex:

	new AsyncRequest(RegisterActivity.this, new IOnFinishWithDataCallback() {
		@Override
		public void onFinish(Object caller) {
			ScreenNameAvailability response = ((ScreenNameAvailability) caller);
			if (response != null && response.isOk() && !response.isAvailable()) {
				tryLaunchScreenNameSuggestion(screenName);
			} 

		}
	}).execute(new ScreenNameAvailability(screenName));

_screenName - the username that the user wants to use._
