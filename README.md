# Despcription
Nowon application coded by Cordova

# How to run
- Firstly, remove android and ios platform

```
npm install
cordova platform rm android
cordova platform rm ios
```
- Second, you need to edit the library
Go to plugin/cordova-plugin-qrscanner/src/android/QRScanner.java and edit this function for it to work perfecly with hide function

```
private void makeOpaque() {
    this.cordova.getActivity().runOnUiThread(new Runnable() {
        @Override
        public void run() {
            webView.getView().setBackgroundColor(Color.WHITE);
        }
    });
    showing = false;
}
```
Go to src/ios/QRScanner.swift and also change to white

```
func makeOpaque(){
    self.webView?.isOpaque = false
    self.webView?.backgroundColor = UIColor.white
}
```
- Third, go to plugin/cordova-plugin-inappbrower/src/ios/CDVInAppBrower.m and set the height of location and toolbox to 0

```
#define    TOOLBAR_HEIGHT 0.0
#define    LOCATIONBAR_HEIGHT 0.0
```
- Finally, add android and ios platform back and build and run them

```
cordova platform add android
cordova platform add ios
```
