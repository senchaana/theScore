# Automation framework

Framework for executing the automation scripts over **theScore** app for iOS platforms

## Command for triggering a specific test suite

**automation.sh**: This file allows the execution of a given TestNG suite defined in a XML

### Parameters

**--file** full path of the app build to be used

**--os** platform, allowed values are "android" or "ios"

**--version** platform version of the device to be used

**--device** Arbitrary name to identify the device

**--suite** name of the xml file containing the TestNG suite to be executed

**--environment (-e)** environment in which the test will be executed, valid values are `stage` and `development`

#### Additional parameters for iOS
**--dudid** Id of the device to be used

**--app_trust_profile** Complete path of an application with the same app signature of CHApp and PlayApp to be installed prior the execution of the suite and avoid the need to trust the application with every new installation

**--ios_cli_install** (optional default false) Boolean that indicates if the installation should be performed by executing *ios-deploy* command instead of the appium default installation


**Example invocation for iOS:**

`sh automation.sh --file /Users/ana.sencha/Projects/PlayApp/app/ios/RC_Build.ipa --os iOS --version 17.4. --device connectedIphone --suite IOS_COMPLETE_SUITE.xml --dudid 00008110-00180D921EB8801E --app_trust_profile /Users/d.montoya/Projects/PlayApp/app/ios/Runner.ipa`

## For triggering the complete suite automatically when a new hockeyapp version is released.

The script **poll_for_new_builds.sh** allows the periodic verification of new releases in hockeyapp, triggering the execution if a new build is found mading use of **automation.sh**, this script requires the following arguments some of which are also passed to **automation.sh**

**NOTE:** this script made use of a python script, therefore python must be previously installed onto the machine.

**--hockeyapp_app_id** Is the identifier assigned in hockeyapp to identify the app build, this can be retrieved in the hockeyapp dashboard

**--os** same as automation.sh

**--version** Same as automation.sh

**--device** Same as automation.sh

#### Additional parameters for iOS

**--dudid** Same as automation.sh

**--app_trust_profile** Same as automation.sh


**Example invocation for Android:**

`sh poll_for_new_builds.sh --os android --version 9 --device connectedAndroid --suite ANDROID_COMPLETE_SUITE.xml --hockeyapp_app_id a7328003470001e8aefe91b5c0c1101d`

**Example invocation for iOS:**

`sh poll_for_new_builds.sh --os ios --version 12.1 --device connectedIphone --dudid 9f82e961e8ac9b8a151efa802b4b5a7956ad501e --app_trust_profile /Users/d.montoya/Projects/PlayApp/app/ios/Runner.ipa --hockeyapp_app_id 7e0a0849bc4f4dbef8cda22aa8d3b0bd`

# Code structure

TBD



