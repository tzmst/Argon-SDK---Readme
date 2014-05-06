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

## Argon API Calls

### 1. Register user:

Ex:

    ArgonSDK.registerUser(context, argonUser, new IOnPreExecuteCallback(), new IOnFinishWithUserCallback(), new IOnExceptionCallback());


_argonUser - an instance of the ArgonUser Object class - in this object you can set the register parameters of the user._


### 2. Login user:

Ex:

    ArgonSDK.loginUser(context, basicUserFields, new IOnPreExecuteCallback(), new IOnFinishWithUserCallback(), new IOnExceptionCallback());

_basicUserFields - and Instance of BasicUserFields, this Object has screenname and password fields needed to login._ _Login request returns an ArgonUserResponse object._

### 3. Get user:
Ex:

    ArgonSDK.getUser(context, argonUser, new IOnPreExecuteCallback(), new IOnFinishWithUserCallback(), new IOnExceptionCallback());

_argonUser - an instance of the ArgonUser Object class - in this object you can set the get information parameters of the user._

### 4. Update user:
Ex:

    ArgonSDK.updateUser(context, argonUser, new IOnPreExecuteCallback(), new IOnFinishWithUserCallback(), new IOnExceptionCallback());

_argonUser - an instance of the ArgonUser Object class - in this object you can set the update parameters of the user._

### 5. Screen name suggestions:
Ex:

    ArgonSDK.getScreenNameSuggestion(context, screenName, new IOnPreExecuteCallback(), new IOnFinishWithSuggestionCallback(), new IOnExceptionCallback());

_screenName - the username that the user wants to use._

### 6. Screen name availability:
_Checks if the user is available_

Ex:

    ArgonSDK.getScreenNameAvailability(context, screenName, new IOnPreExecuteCallback(), new IOnFinishWithAvailabilityCallback(), new IOnExceptionCallback());

_screenName - the username that the user wants to use._


## Argon API Calls - v2

### 7. List topics:
_List topics from server_

Ex:

    ArgonSDK.listTopics(context, offset, limit,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_offset - number of entries to skip._

_limit - number of topics in request (min 0, max 100, default:10)_

### 8. List single topic:
_List single topic from server_

Ex:

    ArgonSDK.listSingleTopic(context, topic,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_topic - instance of Topic Object containing the information to list_

### 9. Create topic:
_Create topic_

Ex:

    ArgonSDK.createTopic(context, topic,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_topic - instance of Topic Object containing the information to create the topic_

### 10. Update topic:
_Update topic_

Ex:

    ArgonSDK.updateTopic(context, topic,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_topic - instance of Topic Object containing the information to update the topic_

### 11. Topic Url Lookup:
_Lookup for a topic_

Ex:

    ArgonSDK.topicUrlLookup(context, topic,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_topic - instance of Topic Object containing the information to lookup for the topic_

### 12. Delete topic:
_Delete a specific topic_

Ex:

    ArgonSDK.deleteTopic(context, topicId,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_topicId - the topic id that you want to delete._

### 13. Undelete topic:
_Undelete a specific topic_

Ex:

    ArgonSDK.undeleteTopic(context, topic,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_topic - instance of Topic Object containing the information to undelete the specific topic_

### 14. List comments:
_List topics from server_

Ex:

    ArgonSDK.listComments(context, comment,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_comment - instance of Comment object, lists the comments specified in the comment topic id togheter with the limit and offset provided_

### 15. List single topic:
_List single comment from server_

Ex:

    ArgonSDK.listSingleComment(context, comment,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_comment - instance of Comment object, lists the comment specified in the comment topic id togheter with the comment id_

### 16. Create comment:
_Create comment_

Ex:

    ArgonSDK.createComment(context, comment,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_comment - instance of Comment Object containing the information to create the comment for the specified topic id_

### 17. Delete comment:
_Delete a specific comment_

Ex:

    ArgonSDK.deleteComment(context, comment,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

### 18. Undelete comment:
_Undelete a specific comment_

Ex:

    ArgonSDK.undeleteComment(context, comment,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

### 19. List ScorePoints:
_Lists scoredPoints for a specific user_

Ex:

    ArgonSDK.listScorePoints(context, limit, offset,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

### 20. Unkown call:
_Make an unkown call to the server. The call is not documented in the standard api_

Ex:

    ArgonSDK.unkownCall(context, unkownObject,  new IOnPreExecuteCallback(), new IOnFinishWithTopicCallback(), new IOnExceptionCallback());

_- unkownObject - an instance of UnkownObject, here you provide the type of call by setting the apiMethod, json information by setting callObject. Togheter with this you have to provide an url for the callUp and the userToken if needed in the request._

### 21. Reset password:
_Reset user password. This sends a sms message to the user on the phone number he registered with. To reset password you can use the **screenName** or the **phone number**_

Ex:

    ArgonSDK.resetPassword(context, screenName,  new IOnPreExecuteCallback(), new IOnFinishWithResetCallback(), new IOnExceptionCallback());

    ArgonSDK.resetPassword(context, phoneNumber,  new IOnPreExecuteCallback(), new IOnFinishWithResetCallback(), new IOnExceptionCallback());

_- screenName - user screen name._

_- phoneNumber - user phone number._

### 22. Reset password with token:
_Resets the password on the server with the received token_

Ex:

    ArgonSDK.resetPasswordWithToken(context, token, password, passwordConfirmation,  new IOnPreExecuteCallback(), new IOnFinishWithResetWithTokenCallback(), new IOnExceptionCallback());

_- screenName - user screen name._

_- phoneNumber - user phone number._

_**The caller callback for the IOnFinishWithResetWithTokenCallback (caller.response) returns an argonUser object**_