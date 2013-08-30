MapKit plugin for iOS and Android
=================================


**************************************

changes for phonegap 3.0 for Android:

update MapKit.java

update config.xml:
	<feature name="MapKit">
        <param name="android-package" value="com.phonegap.plugins.mapkit.MapKit" />
    </feature> 

	(com.phonegap.plugins.mapkit -> it is the package where you have MapKit)
	
	
put the plugin file MapKit-master in plugins directory


**************************************

Uses *Apple Maps* on iOS and *Google Maps v2* on Android

Currently only works/tested on Android and iOS.

![Cordova Map 1](http://i.imgur.com/Mf6oeXal.png)

![Cordova Map 2](http://i.imgur.com/XaaBGeGl.png)

![Cordova Map 3](http://i.imgur.com/3IoDj0Rl.png)

![Cordova Map 4](http://i.imgur.com/Bfzik6Ml.png)


Android specific
----------------

You need a [Google Maps Android v2 API KEY](https://code.google.com/apis/console/) from google and you need to specify it when you install the plugin

You can install this plugin with [plugman](https://npmjs.org/package/plugman)

    plugman --platform android --project android-mapkit-example/ --plugin MapKit --variable API_KEY="YOUR_API_KEY_FROM_GOOGLE"


Sample code
-----------

    var app = {
        showMap: function() {
            var pins = [[49.28115, -123.10450], [49.27503, -123.12138], [49.28286, -123.11891]];
            var error = function() {
              console.log('error');
            };
            var success = function() {
              mapKit.addMapPins(pins, function() { 
                                          console.log('adMapPins success');  
                                      },
                                      function() { console.log('error'); });
            };
            mapKit.showMap(success, error);
        },
        hideMap: function() {
            var success = function() {
              console.log('Map hidden');
            };
            var error = function() {
              console.log('error');
            };
            mapKit.hideMap(success, error);
        },
        clearMapPins: function() {
            var success = function() {
              console.log('Map Pins cleared!');
            };
            var error = function() {
              console.log('error');
            };
            mapKit.clearMapPins(success, error);
        },
        changeMapType: function() {
            var success = function() {
              console.log('Map Type Changed');
            };
            var error = function() {
              console.log('error');
            };
            mapKit.changeMapType(mapKit.mapType.MAP_TYPE_SATELLITE, success, error);
        }
    }

Configuration
-------------

Edit the options in MapKit.js to suit your needs

    this.options = {
      height: 460, // height of the map (width is always full size for now)
      diameter: 1000,   // unused for now
      atBottom: true,   // bottom or top of the webview
      lat: 49.281468,   // initial camera position latitude
      lon: -123.104446  // initial camera position latitude
    };

Sample App
----------

Checkout the sample/ application as a boilerplate!

Missing features
----------------

Info bubbles: Simple info bubbles supported (title, snippet and custom icons for markers). Custom info bubbles not supported (i.e HTML bubbles etc..).
