# fastfiles
This repo has template fastfile for iOS and Android

iOS Instructions:

All parameters are to be exposed as environment variables:
#Parameters : Project_Name, CFBundleIdentifier, Display_Name, BUILD_NUMBER, CFBundleShortVersionString, Apple_Pass, Apple_Id, Apple_Team_Id, Release_Type, CRASHLYTICS_API_TOKEN, CRASHLYTICS_BUILD_SECRET, CRASHLYTICS_GROUP, CRASHLYTICS_BUILD_SECRET

Once environment variables are in place run using the below command:

fastlane ios beta - This builds the app and pushes to the corresponding fabric account

