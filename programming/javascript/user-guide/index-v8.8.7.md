---
layout: default-layout
title: Dynamsoft Barcode Reader JavaScript Edition - v8.8.7 User Guide
description: This is the user guide of Dynamsoft Barcode Reader JavaScript SDK.
keywords: user guide, javascript, js
breadcrumbText: User Guide
noTitleIndex: true
needGenerateH3Content: true
needAutoGenerateSidebar: true
permalink: /programming/javascript/user-guide/index-v8.8.7.html
---

<!--The original doc is hosted here => https://github.com/dynamsoft-docs/barcode-reader-docs-js/blob/preview/programming/javascript/user-guide/index.md -->

# Dynamsoft Barcode Reader for Your Website

Turn your web page into a barcode scanner with just a few lines of code.

![version](https://img.shields.io/npm/v/dynamsoft-javascript-barcode.svg)
![downloads](https://img.shields.io/npm/dm/dynamsoft-javascript-barcode.svg)
![jsdelivr](https://img.shields.io/jsdelivr/npm/hm/dynamsoft-javascript-barcode.svg)
![](https://img.shields.io/snyk/vulnerabilities/npm/dynamsoft-javascript-barcode.svg)

[![](https://img.shields.io/badge/Download-Offline%20SDK-orange)](https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=guide&product=dbr&package=js)

Once integrated, your users can open your website in a browser, access their cameras and read barcodes directly from the video input.

In this guide, you will learn step by step on how to integrate this library into your website.

[GET THE LIBRARY](https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=guide&product=dbr&package=js)

> For back-end barcode reading with Node.js, see [Dynamsoft Barcode Reader for Node](https://www.npmjs.com/package/dynamsoft-node-barcode).

**Table of Contents**

* [Hello World - Simplest Implementation](#hello-world---simplest-implementation)
* [Building your own page](#building-your-own-page)
  + [Include the library](#include-the-library)
  + [Configure the library](#configure-the-library)
  + [Interact with the library](#interact-with-the-library)
* [Requesting A Trial](#requesting-a-trial)
* [System Requirements](#system-requirements)
* [Hosting the Library (optional)](#hosting-the-library-optional)
* [Advanced Usage](#advanced-usage)
* [How to Upgrade](#how-to-upgrade)
* [FAQ](#faq)

**Popular Examples**

* Basic Implementation - [Guide](#hello-world---simplest-implementation) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/master/1.hello-world/1.minimum-code.html) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/1.minimum-code.html?utm_source=guide)
* Angular App - [Guide](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/helloworld-angular.html?ver=8.8.7&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/master/1.hello-world/3.read-video-angular) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/3.read-video-angular/dist/hello-world/?utm_source=guide)
* React App - [Guide](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/helloworld-reactjs.html?ver=8.8.7&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/master/1.hello-world/4.read-video-react) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/4.read-video-react/build/?utm_source=guide)
* Vue App - [Guide](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/helloworld-vuejsv3.html?ver=8.8.7&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/master/1.hello-world/6.read-video-vue3) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/6.read-video-vue3/dist/?utm_source=guide)
* PWA App - [Guide](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/helloworld-pwa.html?ver=8.8.7&utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples/tree/master/1.hello-world/10.read-video-pwa) \| [Run](https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/10.read-video-pwa/helloworld-pwa.html?utm_source=guide)

You can also:

* Try the Official Demo - [Run](https://demo.dynamsoft.com/barcode-reader-js/?utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-demo)
* Try Online Examples - [Run](https://demo.dynamsoft.com/Samples/DBR/JS/index.html?utm_source=guide) \| [Github](https://github.com/Dynamsoft/barcode-reader-javascript-samples)

<br>

## Hello World - Simplest Implementation

Let's start with the "Hello World" example of the library which demonstrates how to use the minimum code to enable a web page to read barcodes from a live video stream.  

* Basic Requirements
  + Internet connection
  + [A supported browser](#system-requirements)
  + Camera access

### Step One: Check the code of the example

The complete code of the "Hello World" example is shown below

```html
<!DOCTYPE html>
<html>

<body>
    <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.8.7/dist/dbr.js"></script>
  <script>
        // initializes and uses the library
        (async () => {
            let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
            scanner.onFrameRead = results => {
                if (results.length > 0) console.log(results);
            };
            scanner.onUnduplicatedRead = (txt, result) => {
                alert(txt);
            };
            await scanner.show();
        })();
    </script>
</body>

</html>
```

<p align="center" style="text-align:center; ">
  <a target="_blank" href="https://github.com/Dynamsoft/barcode-reader-javascript-samples/blob/master/1.hello-world/1.minimum-code.html" title="Code in Github">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="Code in Github" style="width:20px;height:20px;">
  </a>
  &nbsp;
  <a target="_blank" href="https://jsfiddle.net/DynamsoftTeam/pL4e7yrd/" title="Run via JSFiddle">
    <img src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/jsfiddle.svg" alt="Run via JSFiddle" style="width:20px;height:20px;">
  </a>
  &nbsp;
  <a target="_blank" href="https://demo.dynamsoft.com/Samples/DBR/JS/1.hello-world/1.minimum-code.html?utm_source=guide" title="Run in Dynamsoft">
    <img src="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/svgs/solid/circle-play.svg" alt="Run in Dynamsoft" style="width:20px;height:20px;">
  </a>
  &nbsp;
  <a target="_blank" href="https://tst.dynamsoft.com/public/download/dbr/browser/code/helloworld-v8.8.7.zip?utm_source=guide" title="Download from Dynamsoft">
    <img src="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/svgs/solid/download.svg" alt="Download from Dynamsoft" style="width:20px;height:20px; ">
  </a>
</p>

-----

*About the code*

  + `createInstance()`: This method creates a `BarcodeScanner` object. This object can read barcodes directly from a video input with the help of its interactive UI (hidden by default) and the <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices" title="MediaDevices interface">MediaDevices interface</a>.

  + `onFrameRead`: This event is triggered every time the library finishes scanning a video frame. The `results` object contains all the barcode results that the library have found on this frame. In this example, we print the results to the browser console.

  + `onUnduplicatedRead`: This event is triggered when the library finds a new barcode, which is not a duplicate among multiple frames. `txt` holds the barcode text value while `result` is an object that holds details of the barcode. In this example, an alert will be displayed for this new barcode.

  + `show()`: This method brings up the built-in UI of the `BarcodeScanner` object and starts scanning.

### Step Two: Test the example

Open the example page in a browser, allow the page to access your camera and the video will show up on the page. After that, you can point the camera at a barcode to read it.

When a barcode is decoded, you will see the result text pop up and the barcode location will be highlighted in the video feed. 

  > For first use, you may need to wait a few seconds for the library to initialize.

*Note*:

  + The library requires a license to work. However, when no license is specified in the code, a [free 1-day public trial license](https://www.dynamsoft.com/license-server/docs/about/terms.html?ver=latest#public-trial-license?utm_source=guide) will automatically be used during which you can make initial evaluation of the library to decide whether or not you want to evaluate it further. If you do, you can [request a 30-day private trial license](#requesting-a-trial).
    > Network connection is required for the free public trial license to work.

If the test doesn't go as expected, you can check out the [FAQ](#faq) or [contact us](https://www.dynamsoft.com/company/contact/?utm_source=guide).

<br>

## Building your own page

### Include the library

#### Use a CDN

The simplest way to include the library is to use either the [jsDelivr](https://jsdelivr.com/) or [UNPKG](https://unpkg.com/) CDN. The "hello world" example above uses **jsDelivr**.

* jsDelivr

  ```html
  <script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.8.7/dist/dbr.js"></script>
  ```

* UNPKG  

  ```html
  <script src="https://unpkg.com/dynamsoft-javascript-barcode@8.8.7/dist/dbr.js"></script>
  ```

#### Host the library yourself

Besides using the CDN, you can also download the library and host its files on your own website / server before including it in your application.

A few ways to download the library:

* From the website

  [Download the JavaScript Package](https://www.dynamsoft.com/barcode-reader/downloads/?utm_source=guide)

* yarn

  ```cmd
  $ yarn add dynamsoft-javascript-barcode
  ```

* npm

  ```
  $ npm install dynamsoft-javascript-barcode --save
  ```

Depending on how you downloaded the library and where you put it, you can typically include it like this:

```html
<script src="/dbr-js-8.8.7/dist/dbr.js"></script>
```

or

```html
<script src="/node_modules/dynamsoft-javascript-barcode/dist/dbr.js"></script>
```

Read more on [how to host the library](#hosting-the-library-optional).

### Configure the library

Before using the library, you need to configure a few things.

#### Specify the license

The library requires a license to work, use the API `license` to specify it.

```javascript
Dynamsoft.DBR.BarcodeReader.license =
  "YOUR-ORGANIZATION-ID or YOUR-HANDSHAKECODE or AN-OFFLINE-LICENSE or ANY-OTHER-TYPE-OF-SUPPORTED-LICENSE-STRING";
```
  
Or

```html
<script src="https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.8.7/dist/dbr.js"
  data-license="YOUR-ORGANIZATION-ID or YOUR-HANDSHAKECODE or AN-OFFLINE-LICENSE or ANY-OTHER-TYPE-OF-SUPPORTED-LICENSE-STRING"></script>
```

*Note*:

* When specified by YOUR-ORGANIZATION-ID or YOUR-HANDSHAKECODE, the license is an online license and a network connection to Dynamsoft License Server is required for it to work.
* In most cases, online licenses are offered. If you want to use an offline license, you can [contact us](https://www.dynamsoft.com/company/contact/?utm_source=guide).
* If nothing is specified like the above "hello world" example, a [free 1-day public trial license](https://www.dynamsoft.com/license-server/docs/about/terms.html?ver=latest#public-trial-license?utm_source=guide) will be automatically used. This license requires a network connection.
  

#### Specify the location of the "engine" files

If the engine files (*.worker.js, *.wasm.js and *.wasm, etc.) are not in the same location with the main library file (dbr.js), you can use the API `engineResourcePath` to specify the engine path, for example:

```javascript
//The following code uses the jsDelivr CDN, feel free to change it to your own location of these files
Dynamsoft.DBR.BarcodeScanner.engineResourcePath = "https://cdn.jsdelivr.net/npm/dynamsoft-javascript-barcode@8.8.7/dist/";
```

This configuration is usually required with frameworks like Angular or React where dbr.js is compiled into another file.

### Interact with the library

#### Create a `BarcodeScanner` object

You can use one of two classes ( `BarcodeScanner` and `BarcodeReader` ) to interact with the library. `BarcodeReader` is a low-level class that processes images directly. `BarcodeScanner`, on the other hand, inherits from `BarcodeReader` and provides high-level APIs and a built-in GUI to allow continuous barcode scanning on video frames. We'll focus on `BarcodeScanner` in this guide.

To use the library, we first create a `BarcodeScanner` object.

```javascript
let scanner = null;
try {
    scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
} catch (ex) {
    console.error(ex);
}
```

Tip: When creating a `BarcodeScanner` object within a function which may be called more than once, it's best to use a "helper" variable to avoid double creation such as `pScanner` in the following code

```javascript
let pScanner = null;
document.getElementById('btn-scan').addEventListener('click', async () => {
    try {
        const scanner = await (pScanner = pScanner || Dynamsoft.DBR.BarcodeScanner.createInstance());
    } catch (ex) {
        console.error(ex);
    }
});
```

#### Configure the `BarcodeScanner` object

Let's take a look at the following code snippets first:

```javascript
// set which camera and what resolution to use
let allCameras = await scanner.getAllCameras();
await scanner.setCurrentCamera(allCameras[0].deviceId);
await scanner.setResolution(1280, 720);
```

```javascript
// set up the scanner behavior
let scanSettings = await scanner.getScanSettings();
// disregard duplicated results found in a specified time period (in milliseconds)
scanSettings.duplicateForgetTime = 5000;
// set a scan interval in milliseconds so the library may release the CPU from time to time
scanSettings.intervalTime = 100;
await scanner.updateScanSettings(scanSettings);
```

```javascript
// use one of the built-in RuntimeSetting templates: "single" (decode a single barcode, the default mode), "speed", "balance" and "coverage"
await scanner.updateRuntimeSettings("speed");

// make changes to the template. The code below demonstrates how to specify enabled symbologies
let runtimeSettings = await scanner.getRuntimeSettings();
runtimeSettings.barcodeFormatIds = Dynamsoft.DBR.EnumBarcodeFormat.BF_ONED | Dynamsoft.DBR.EnumBarcodeFormat.BF_QR_CODE;
await scanner.updateRuntimeSettings(runtimeSettings);
```

[Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/yfkcajxz/)

As you can see from the above code snippets, there are three types of configurations:

* `get/updateVideoSettings`: Configures the data source, i.e., the camera. These settings include which camera to use, the resolution, etc. Learn more <a href="https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia#Syntax" target="_blank" title="here">here</a>.

* `get/updateScanSettings`: Configures the behavior of the scanner which includes `duplicateForgetTime`,  `intervalTime` and `filter`, etc.

* `get/updateRuntimeSettings`: Configures the decode engine with either a built-in template or a comprehensive `RuntimeSettings` object. For example, the following uses the built-in "speed" settings with updated `localizationModes`.

> Find the full list of these settings <a href="https://www.dynamsoft.com/barcode-reader/programming/javascript/api-reference/global-interfaces.html?utm_source=guide#runtimesettings" target="_blank" title="here">here</a>. 

  ```javascript
  await barcodeScanner.updateRuntimeSettings("speed");
  //await barcodeScanner.updateRuntimeSettings("balance"); //alternative
  //await barcodeScanner.updateRuntimeSettings("coverage"); //alternative
  let settings = await barcodeScanner.getRuntimeSettings();
  settings.localizationModes = [
      Dynamsoft.DBR.EnumLocalizationMode.LM_CONNECTED_BLOCKS,
      Dynamsoft.DBR.EnumLocalizationMode.LM_SCAN_DIRECTLY,
      Dynamsoft.DBR.EnumLocalizationMode.LM_LINES, 0, 0, 0, 0, 0
  ];
  await barcodeScanner.updateRuntimeSettings(settings);
  ```

  Try in [JSFiddle](https://jsfiddle.net/DynamsoftTeam/f24h8c1m/).

  See also [settings samples](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/parameter-settings.html?ver=8.8.7&utm_source=guide).

#### Customize the UI

The built-in UI of the `BarcodeScanner` object is defined in the file `dist/dbr.scanner.html` . There are a few ways to customize it:

* Modify the file `dist/dbr.scanner.html` directly. 

  This option is only possible when you host this file on your own web server instead of using a CDN.

* Copy the file `dist/dbr.scanner.html` to your application, modify it and use the the API `defaultUIElementURL` to set it as the default UI.

  ```javascript
  Dynamsoft.DBR.BarcodeScanner.defaultUIElementURL = "THE-URL-TO-THE-FILE";
  ```

  
  > You must set `defaultUIElementURL` before you call `createInstance()` .

* Append the default UI element to your page, customize it before showing it.

  ```html
  <div id="div-video-container"></div>
  ```

  ```javascript
  document.getElementById('div-video-container').appendChild(scanner.getUIElement());
  document.getElementsByClassName('dce-btn-close')[0].hidden = true; // Hide the close button
  ```

* Build the UI element into your own web page and specify it with the API `setUIElement(HTMLElement)`.

  + Embed the video

    ```html
    <div id="div-video-container" style="position:relative;width:100%;height:70vh;">
        <video class="dce-video" playsinline="true" muted style="position:absolute;left:0;top:0;width:100%;height:100%;"></video>
    </div>
    <script>
        (async () => {
            let scanner = await Dynamsoft.DBR.BarcodeScanner.createInstance();
            await scanner.setUIElement(document.getElementById('div-video-container'));
            scanner.onFrameRead = results => {
                console.log(results);
            };
            scanner.onUnduplicatedRead = (txt, result) => {
                alert(txt);
            };
            await scanner.show();
        })();
    </script>
    ```

    > The video element must have the class `dce-video` .

    [Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/2jzeq1r6/)

  + Add the camera list and resolution list
  

    If the class names for these lists match the default ones, `dce-sel-camera` and `dce-sel-resolution` , the library will automatically populate the lists and handle the camera/resolution switching.

    ```html
    <select class="dce-sel-camera" style="position:absolute;left:0;top:0;"></select>
    ```

    [Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/nbj75vxu/)

    ```html
    <select class="dce-sel-resolution" style="position:absolute;left:0;top:20px;"></select>
    ```

    [Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/25v08paf/)

    > By default, 8 hard-coded resolutions are populated as options. You can show only a custom set of options by hardcoding them.

    ```html
    <select class="dce-sel-resolution" style="position:absolute;left:0;top:20px;">
        <option class="dce-opt-gotResolution" value="got"></option>
        <option data-width="1920" data-height="1080">1920 x 1080</option>
        <option data-width="1280" data-height="720">1280 x 720</option>
        <option data-width="640" data-height="480">640 x 480</option>
    </select>
    ```

    [Try in JSFiddle](https://jsfiddle.net/DynamsoftTeam/tnfjks4q/)

    > Generally, you need to provide a resolution that the camera supports. However, in case a camera does not support the specified resolution, it usually uses the nearest supported resolution. As a result, the selected resolution may not be the actual resolution used. In this case, add an option with the class name `dce-opt-gotResolution` (as shown above) and the library will then use it to show the actual resolution.

See also [UI customization samples](https://www.dynamsoft.com/barcode-reader/programming/javascript/samples-demos/ui-customization.html?ver=8.8.7&utm_source=guide).

<br>

## Requesting a Trial

You can request a 30-day free private trial via the [customer portal](https://www.dynamsoft.com/customer/license/trialLicense?utm_source=guide&product=dbr&package=js). Or you can [contact our support team](https://www.dynamsoft.com/company/contact/?utm_source=github) to get a free trial license.

Since v8.2.5, a free public trial license is used by default if no license is specified.

<br>

## System Requirements

This library requires the following features which are supported by all modern mainstream browsers:

* `WebAssembly`,  `Blob`,  `URL`/`createObjectURL`,  `Web Workers`
    

  The above four features are required for the library to work.

* `MediaDevices`/`getUserMedia`

  This API is only required for in-browser video streaming. If a browser does not support this API, the [Single Frame Mode](https://www.dynamsoft.com/barcode-reader/programming/javascript/api-reference/BarcodeScanner.html?ver=8.8.7&utm_source=guide#singleframemode) will be used automatically. If the API exists but doesn't work correctly, the Single Frame Mode can be used as an alternative way to access the camera.

The following table is a list of supported browsers based on the above requirements:

  Browser Name | Version
  :-: | :-:
  Chrome | v57+ (v59+ on Android/iOS<sup>1</sup>)
  Firefox | v52+ (v55+ on Android/iOS<sup>1</sup>)
  Edge<sup>2</sup> | v16+
  Safari<sup>3</sup> | v11+

  <sup>1</sup> iOS 14.3+ is required for camera video streaming in Chrome and Firefox or Apps using webviews.

  <sup>2</sup> On Edge, due to strict Same-origin policy, you must host the library files on the same domain as your web page. 
  
  <sup>3</sup> Safari 11.2.2 ~ 11.2.6 are not supported.

Apart from the browsers, the operating systems may impose some limitations of their own that could restrict the use of the library. Browser compatibility ultimately depends on whether the browser on that particular operating system supports the features listed above.

<br>

## Hosting the library (optional)

### Step One: Deploy the dist folder

Once you have downloaded the library, you can locate the "dist" directory and copy it to your server (usually as part of your website / web application). 

Some of the files in this directory:

* `dbr.js` // The main library file
* `dbr.mjs` // For using the library as a module (`<script type="module">`)
* `dbr.scanner.html` // Defines the default scanner UI
* `dbr-<version>.worker.js` // Defines the worker thread for barcode reading
* `dbr-<version>.wasm.js` // Compact edition of the library (.js)
* `dbr-<version>.wasm` // Compact edition of the library (.wasm)
* `dbr-<version>.full.wasm.js` // Full edition of the library (.js)
* `dbr-<version>.full.wasm` // Full edition of the library (.wasm)

### Step Two: Configure the Server

* Set the MIME type for `.wasm` as `application/wasm` on your webserver.
  
  The goal is to configure your server to send the correct Content-Type header for the wasm file so that it is processed correctly by the browser.

  Different types of webservers are configured differently, for example:

  + <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Learn/Server-side/Apache_Configuration_htaccess#media_types_and_character_encodings" title="Apache">Apache</a>
  + <a target="_blank" href="https://docs.microsoft.com/en-us/iis/configuration/system.webserver/staticcontent/mimemap" title="IIS">IIS</a>
  + <a target="_blank" href="https://www.nginx.com/resources/wiki/start/topics/examples/full/#mime-types" title="NGINX">NGINX</a>

* Enable HTTPS

  Due to the browser <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts" title="security restriction">security restriction</a> on camera video streaming access, a secure HTTPS connection is required to use the library with camera.

  > For convenience, self-signed certificates can be used during development and testing.

### Step Three: Include the library from the server

Now that the library is hosted on your server, you can include it accordingly.

```html
<script src="https://www.yourwebsite.com/dynamsoft-javascript-barcode/dist/dbr.js"></script>
```

Optionally, you may also need to [specify the location of the "engine" files](#specify-the-location-of-the-engine-files).

<br>

## Advanced Usage

In addition to the above basic settings, the library has many more settings and options that you can adjust to best suit your usage. To read more, please see [advanced usage](https://www.dynamsoft.com/barcode-reader/programming/javascript/user-guide/advanced-usage.html?ver=8.8.7&utm_source=guide).

<br>

## How to Upgrade

If you want to upgrade the library from an old version to a newer one, please see [how to upgrade](https://www.dynamsoft.com/barcode-reader/programming/javascript/upgrade-guide/?ver=8.8.7&utm_source=guide).

<br>

## FAQ

### Can I open the web page directly from the hard drive?

Yes, for simple testing purposes, it's perfectly fine to open the file directly from the hard drive. However, you might encounter some issues in doing so (like unable to access the camera, etc.). The recommendation is to deploy this page to your web server and run it over **HTTPS**. If you don't have a ready-to-use web server but have a package manager like *npm* or *yarn*, you can set up a simple HTTP server in minutes. Check out [http-server on npm](https://www.npmjs.com/package/http-server). 

### Why can't I use my camera?

If you open the web page as `file:///` or `http://` , the camera may not work and you see the following error in the browser console:

> [Deprecation] getUserMedia() no longer works on insecure origins. To use this feature, you should consider switching your application to a secure origin, such as HTTPS. See https://goo.gl/rStTGz for more details.

* In Safari 12 the equivalent error is:

> Trying to call getUserMedia from an insecure document.

You get this error because the API <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia" title="getUserMedia">getUserMedia</a> requires HTTPS to access the camera.

* If you use Chrome or Firefox, you might not get the error because these two browsers allow camera access via file:/// and http://localhost.

To make sure your web application can access the camera, please configure your web server to support HTTPS. The following links may help.

  + NGINX: <a target="_blank" href="https://nginx.org/en/docs/http/configuring_https_servers.html" title="Configuring HTTPS servers">Configuring HTTPS servers</a>
  + IIS: <a target="_blank" href="https://aboutssl.org/how-to-create-a-self-signed-certificate-in-iis/" title="Create a Self Signed Certificate in IIS">Create a Self Signed Certificate in IIS</a>
  + Tomcat: <a target="_blank" href="https://dzone.com/articles/setting-ssl-tomcat-5-minutes" title="Setting Up SSL on Tomcat in 5 minutes">Setting Up SSL on Tomcat in 5 minutes</a>
  + Node.js: <a target="_blank" href="https://nodejs.org/docs/v0.4.1/api/tls.html" title="npm tls">npm tls</a>

### Accounting for newline characters in the barcode result

When it comes to HTML, newline characters ( `\n` ) are not interpreted as they normally would. Therefore, if a barcode result contains a newline character, and you display the result in an modal dialogue box or some other text elements, then the newline character will probably be ignored.

There are two ways in which you can resolve this:
1. Wrap the element used to display the result in a `<pre>` element.
2. Manually replace each `\n` character in the result with `<br>`
