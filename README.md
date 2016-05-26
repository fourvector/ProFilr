# ProFilr
<p align="center">
<img src="https://github.com/rahulbelekar/ProFilr/blob/master/Resources/Icon.png" alt="Icon"/>
</p>
<H1 align="center">ProFilr</H1>
<p align="center">
<img src="https://github.com/rahulbelekar/ProFilr/blob/master/Resources/License.svg"
alt="GitHub license"/>

Apps that require filling of large forms to accept data gets less traction from users, as users dont like to key in alot of data. We have our app on app store `ProFilr` were the user keys in data, this data is encrypted and stored. This `ProFilr-Framework` allows your app to retrive data from the `ProFilr` app and auto fill your app with data which will save alot of users key strokes.


##Key Features

1) `Simple Integration`

2) `Minimal Lines Implementation`

##Installation

In your form view Controller, just import ProFilr framework and add the following code to fetch the data from ProFilr Application. You will have to implement `ProFilrDelegate` to receive the data.

```swift
import ProFilr
class ViewController: UIViewController, ProFilrDelegate {

....Your Code...
let pFill = ProFilr()
....Your Code...

@IBAction func autoFillFromProFilr(sender: UIButton) {
       pFill.delegate = self
       pFill.profileInformation()
}

//MARK: ProFilr Delegate
    func ProFilrRecievedData(proFilr: ProFilr, data: ProfileDetails) {
        self.imageView.image = data.profileData.profilePic
        //Assign all values recieved from ProFilr application to your UI objects
    }
```

##Properties and functions usage:-

You can find some documentation about properties, methods and their uses [here]().


LICENSE
---
Distributed under the MIT License.

Author
---
If you wish to contact me, email at: rahul@fourvector.in
