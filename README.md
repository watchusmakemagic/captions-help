# captions-help

##  Contributing captions

There are multiple methods you can use to provide captions into Caption Portal and these methods can be used in combination.


### Entering captions with a keyboard

Use the link you were provided to navigate to your Caption Portal. Once your Caption Portal has loaded, click the `Transcribe/Caption` button in the main menu.

A `Transcriber` text input area will be visible.

Any text that you type into the text input area will be presented to all distribution outputs whenever any one of the following constraints is met,

* the number of characters in the text area exceeds 40 characters when the space button is pressed
* the sentence ends, I.e. a full stop, exclamation mark or question mark is entered
* a carriage return is entered

### Using pre-formatted captions

#### Uploading a WebVTT file

Caption Portal supports pre-formatted captions in [WebVTT](https://developer.mozilla.org/en-US/docs/Web/API/WebVTT_API) format. 

To upload a WebVTT file, navigate to your Caption Portal and click the `WebVTT` button in the main menu. 

![Add a WebVTT file](https://cdn.watchusmakemagic.com/help/add_webvtt.gif)

Click the `Choose file` button and select a WebVTT file from your machine and then click the `UPLOAD WEBVTT` button.


> If you receive an error message - double check the format of your WebVTT file.

#### Triggering pre-formatted captions

Navigate to your Caption Portal, or click the `Transcribe/Caption` button in the main menu.

If you have uploaded a caption file (a WebVTT file) you will see the captions displayed one by one.

You can trigger the captions by clicking them one at a time, or by using the `F9` button to advance to the next caption, or the `F10` button to move backwards.


#### Removing a WebVTT file

To remove a WebVTT file, navigate to your Caption Portal and click the `WebVTT` button in the main menu. 

Click the `REMOVE WEBVTT` button and your pre-formatted captions will be removed from Caption Portal.

## Distributing Captions

There are multiple methods you can use to deliver captions to viewers using Caption Portal. These methods can be used in combination.

### Closed-captions (OBS)

[608 closed captions](https://en.wikipedia.org/wiki/EIA-608) are supported on many video distribution platforms that support RTMP ingest, including AWS IVS, Facebook, Vimeo, Twitch, YouTube and many others. At the time of writing (July 2021) [OBS](https://obsproject.com/) on Windows can be used to insert closed caption data in the form of 608 closed captions, which are delivered to OBS by Caption Portal via OBS's WebSockets interface.

When using Caption Portal to provide captions to OBS, WebSockets messages are sent from your browser to each instance of OBS. This means that,

* your browser must have your Caption Portal open in one tab
* your browser must be on the same network as your OBS instances, or able to communicate with them through any firewalls
* the sources of your caption data (such as a speech to text reporter) can be be anywhere that can access Caption Portal's servers, including on a different network


#### Setup OBS WebSockets

To insert closed captions with OBS, for each instance of OBS,

* install [OBS](https://obsproject.com/) 
* install the [OBS WebSockets plugin](https://github.com/Palakis/obs-websocket) plugin
* enable OBS's WebSockets interface by using the WebSockets interface in OBS's `Tools` menu

![Enable WebSockets interface](https://cdn.watchusmakemagic.com/help/enable_websockets_interface.png)

#### Setup your browser to send messages to OBS

Navigate to your Caption Portal and click the `Closed-captions (OBS)` button in the main menu.

Enter the details (the IP address and port, and password) of up to two OBS instances.

> You do not need to save the data you enter, it is stored automatically in a cookie in your browser - this is important, as if you change your browser or delete your local cache you will need to enter this information again!

![Enter OBS details](https://cdn.watchusmakemagic.com/help/enable_websockets_obs_in_caption_portal.png)

#### Troubleshooting Closed-caption OBS issues

If captions are not appearing on your video distribution platform, enable debug logging of the OBS WebSockets interface and view the current OBS log.

![Enable WebSockets debugging in OBS](https://cdn.watchusmakemagic.com/help/enable_websockets_interface_debugging.png)

![View the OBS log](https://cdn.watchusmakemagic.com/help/view_obs_log.png)

If log entries are not being created in the OBS log, double check the OBS instance details are correct in Caption Portal. If the details are correct, double check that the machine running the browser window viewing Caption Portal has access over the network to the OBS instance.

If log entries are being created in the OBS log, then the issue is likely between your instance of OBS and the video distribution platform. Double check that your video distribution platform/s are configured to use 608 captions, this varies between platforms.

### Open-captions

The example below describes how to set up open captions from Caption Portal in OBS. 

Head to your Caption Portal and click the `Open-captions` in the main menu.

You will need to copy one of the pre-formatted links or create your own. To get started, we recommend you copy the Link of the `Green chroma key, white text, center align` as indicated below - on most platforms you can right-click to do this,

![Copy an open caption link](https://cdn.watchusmakemagic.com/help/copy_open_caption_link.png)

In OBS, add a new `Browser` source to your OBS scene,

![Add new Browser source](https://cdn.watchusmakemagic.com/help/add_new_browser_source.png)

Paste in the Open-caption URL you copied from Caption Portal into the settings of the `Browser` source.

If you unsure if the size to configure, we would recommend 1920 by 100 pixels is sensible for widescreen presentations.

![Add new Browser source settings](https://cdn.watchusmakemagic.com/help/add_browser_source_settings.png)

Move the `Browser` source to the desired position.

Enter a caption so you have some content to test with.

Right-click the `Browser` source in OBS's Sources and configure a filter by clicking `Filters`.

Add an Effect filter by clicking the `+` icon and choose 'Chroma Key'

![Add new Browser source](https://cdn.watchusmakemagic.com/help/add_chroma_key.png)

Enter a name that makes sense to you (e.g. `Captions`) and progress to the next screen.

Ensure that Key Colour Type is 'Green' and then adjust the 'Similarity (1-1000)' slider until only the caption is visible and click 'Close'

![Open captions are visible in OBS](https://cdn.watchusmakemagic.com/help/open_caption_visible_in_obs.png)

### Viewing captions on devices

#### Viewer (for personal devices)

Caption Portal can present captions to an In-person or Hybrid audience who wish to view captions on personal devices such as mobile phones or tablets. You can direct these viewers to a URL in the Caption Portal by copying the URL of the `Viewer` option in the main menu, or by sharing the QR code available from the `QR Code` option in the main menu. 

The following query parameters can be used to customise the display,

* `font_color` e.g. blue
* `font_family` e.g. monospace
* `background_color` e.g. black
* `text_align` e.g. left
* `viewercontrols` e.g. none

#### Scroller (for displays, televisions and video walls)

Caption Portal can present captions to an In-person or Hybrid audience who wish to view captions on a display, television or video wall. You can direct these viewers to a URL in the Caption Portal by copying the URL of the `Scroller` option in the main menu, or by sharing the QR code available from the `QR Code` option in the main menu.

The following query parameters can be used to customise the display,

* `font_color` e.g. blue
* `font_family` e.g. monospace
* `background_color` e.g. black
* `text_align` e.g. left
* `viewercontrols` e.g. none
* `tween_speed` e.g. 1200


#### Configuring Webhook URLs

If you wish to deliver captions to Zoom or another service that support the POST'ing of captions via plain text, head to `Webhook URLs` page available in the Main Menu of your Caption Portal.

Enter Webhook URLs, one per line.

> You do not need to save the data you enter, it is stored automatically in a cookie in your browser - this is important, as if you change your browser or delete your local cache you will need to enter this information again!

Caption Portal will forward captions to your webhook from the Caption Portal server, not from your browser - *note this is different to the Closed-caption OBS interface*, though your browser window must be open for this to function.

