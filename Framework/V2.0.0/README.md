# ProFilr
<p align="center">
<img src="https://github.com/rahulbelekar/ProFilr/blob/master/Resources/Icon.png" alt="Icon"/>
</p>
<H1 align="center">ProFilr</H1>

Apps that require filling of large forms to accept data gets less traction from users, as users dont like to key in alot of data. We have our app on app store `ProFilr` were the user keys in data, this data is encrypted and stored. This `ProFilr-Framework` allows your app to retrive data from the `ProFilr` app and auto fill your app with data which will save alot of users key strokes. App Store Link: https://itunes.apple.com/us/app/profilr/id1124576875


##Key Features

1) `Simple Integration`

2) `Minimal Lines Implementation`

##Installation

####Manual Installation
- Download ProFilr.framework file.
- Go to your XCode Project's `General` settings. Drag/Add the downaloaded ProFilr.framework to the `Embedded Binaries` section. Make sure `Copy items if needed` is selected and click Finish.

<!--####Setup URLSchemes-->

<!--It is necessary to setup URLScheme, so that your application is able to communicate with ProFilr App.-->

<!--- Go to your XCode Project and open info.plist file in `Source Code` Mode.-->
<!--- Add the following code under the main `<dict>` tag.-->
<!--```URLScheme-->
<!--<key>CFBundleURLTypes</key>-->
<!--<array>-->
<!--<dict>-->
<!--<key>CFBundleURLSchemes</key>-->
<!--<array>-->
<!--<string>$(PRODUCT_BUNDLE_IDENTIFIER)</string>-->
<!--</array>-->
<!--<key>CFBundleURLName</key>-->
<!--<string></string>-->
<!--</dict>-->
<!--</array>-->
<!--<key>LSApplicationQueriesSchemes</key>-->
<!--<array>-->
<!--<string>ProFilr</string>-->
<!--</array>-->
<!--```-->

<!--- If you already have URLSchemes setup, may be for another app. All you need to do is add an array item under CFBundleURLSchemes and  LSApplicationQueriesSchemes as follows-->

<!--```URLScheme-->
<!--<key>CFBundleURLTypes</key>-->
<!--<array>-->
<!--<dict>-->
<!--<key>CFBundleURLSchemes</key>-->
<!--<array>-->
<!--<string>Your Other App String</string>-->
<!--<string>$(PRODUCT_BUNDLE_IDENTIFIER)</string>-->
<!--</array>-->
<!--<key>CFBundleURLName</key>-->
<!--<string></string>-->
<!--</dict>-->
<!--</array>-->
<!--<key>LSApplicationQueriesSchemes</key>-->
<!--<array>-->
<!--<string>Your Other App String</string>-->
<!--<string>ProFilr</string>-->
<!--</array>-->
<!--```-->

<!--Reference screenshots-->
<!--![info.plist](https://github.com/rahulbelekar/ProFilr/blob/master/Resources/URLScheme1.png)-->
<!--![info.plist](https://github.com/rahulbelekar/ProFilr/blob/master/Resources/URLScheme2.png)-->

##Code

In your form view Controller, just import ProFilr framework and add the following code to fetch the data from ProFilr Application. You will have to implement `ProFilrDelegate` to receive the data.

```swift
import ProFilr
class ViewController: UIViewController, ProFilrDelegate {

....Your Code...
let pFill = ProFilr()
....Your Code...

@IBAction func autoFillFromProFilr(sender: UIButton) {
pFill.profileInformation(self, requiredInfo: [.All])
}

//MARK: ProFilr Delegate
func proFilr(proFilr: ProFilr, didReturnAllInfo info: ProfileDetails) {
self.imageView.image = data.profileData.profilePic
//Assign all values recieved from ProFilr application to your UI objects
}
```

##Properties and functions usage:-
```swift
//profileInformation method takes an array of enum as input, you can specify specific info to be fetched.
public enum ProFilrDataInfo : String {
    case Personal //Personal data will be fetched. eg: Name, DOB, Profile Image etc
    case Contact //Contacts will be fetched. eg: Mobile, Landline, Email
    case Address //Address data will be fetched.
    case CardPayment //Credit/Debit card details will be fetched
    case IdentificationDocument //ID card details will be fetched, this does not include documents only ID and number.
    case Credentials //User credentials will be fetched.
    case All
}

//Implement specific delegate methods to fetch specific details
func proFilr(proFilr: ProFilr, didReturnAllInfo info: ProfileDetails) {
//Implement for fetching all data, If all data is requested no need to implement the below methods. All relevant data will be available in this method.
}
func proFilr(proFilr: ProFilr, didReturnPersonalInfo personalInfo: ProfileData) { 
//Implement for fetching Personal Data.
}
func proFilr(proFilr: ProFilr, didReturnContactInfo contactInfo: ProfileContact) { 
//Implement for fetching Contact info.
}
func proFilr(proFilr: ProFilr.ProFilr, didReturnCredential credential: ProFilr.ProfileCredentials) {
//Implement for fetching Credential info.
}
func proFilr(proFilr: ProFilr.ProFilr, didReturnAddressInfo addressInfo: ProFilr.ProfileAddress) {
//Implement for fetching Address info.
}
func proFilr(proFilr: ProFilr.ProFilr, didReturnCardInfo cardInfo: ProFilr.ProfileCardDetails) { 
//Implement for fetching Credit/Debit card info.
}
func proFilr(proFilr: ProFilr.ProFilr, didReturnIdentificationInfo idInfo: ProFilr.ProfileIdentificationDetails) {
//Implement for fetching Identification info.
}
```
<!--You can find some documentation about properties, methods and their uses [here]().-->


<!--LICENSE-->
<!------->
<!--Distributed under the MIT License.-->

Author
---
If you wish to contact me, email at: rahul@fourvector.in
