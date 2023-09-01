# Installation
There are 2 options to install ArenaSDK into your project :
- Download .tgz package and install from Unity Package Manager using "add package from tarball..." option
- Install from Unity Package Manager using "add package from git URL"

# API
ArenaSDK provides several tools for developers such as user registration, authorization and access to leader boards.  
First of all add ArenaSDKManager to your inital scene and make sure that there will be only one instance of it.  
Fill up your game alias and server access token fields.  

- MaxUserLoginAttemptCount  
In order to avoid manual updating tokens ArenaSDKManager will update access token automatically every time it becomes expired.  
If you need to get or update tokens manually you can use UpdateAccessToken function.

ArenaSDKManager is a singleton and you can access it using ArenaSDKManager.Instance property.

- #### ArenaSDKManager.Instance.RegisterUser  
To register new user use ArenaSDKManager.Instance.RegisterUser function.  
After calling this function you have to handle callback which will contain IResponse object.  
All possible unique IResponse object types are described in method info. All functions could return common fail responses such as UnityWebRequestFail or ServerFail.  
If registration was successful IResponse object will be of type UserInfo.
This info will be automatically saved by ArenaSDKManager 
and you can access it later using ArenaSDKManager.UserInfo property.  
Also UserInfo will be automatically downloaded and cached every time when user passes authorization (and when passes registration).  
If registration process will fail IResponse object will be of type IFailResponse.  

Samples of handling different responses are available in samples folder.

- #### ArenaSDKManager.Instance.SendConfirmationCode
After registration proccess confirmation code will be sent automatically. But you can request confirmation code again.

- #### ArenaSDKManager.Instance.ConfirmEmail
Use this function during registration process to validate code that was sent to user's email. 

- #### ArenaSDKManager.Instance.AuthorizeUser
Use this function to authorize user.

- #### ArenaSDKManager.Instance.LoadLeaderBoard
Load game's leaderboard using leaderboard alias.

- #### ArenaSDKManager.Instance.UpdateUserStatistics
Update user's scores on different leaderboards.

- #### ArenaSDKManager.Instance.LoadUserInfo
Manually load UserInfo. You can use this function when ArenaSDKManager.Instance.OnUserInfoLoadFailed is fired.

- #### ArenaSDKManager.Instance.UpdateAccessToken
Manually request access token. You can use this function when ArenaSDKManager.Instance.OnAccessTokenUpdateFailed is fired.