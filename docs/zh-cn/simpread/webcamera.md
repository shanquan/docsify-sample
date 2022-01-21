> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [davidwalsh.name](https://davidwalsh.name/browser-camera)

> Access the desktop camera and video using HTML, JavaScript, and Canvas. The camera may be controlled ......

The method for getting access to camera was initially `navigator.getUserMedianavigator.mediaDevices.getUserMedia`.

Browser vendors have recently ruled that `getUserMedia` should only work on `https:` protocol. You'll need a SSL certificate for this API to work.

[![](https://davidwalsh.name/demo/camera-pic.jpg)](https://davidwalsh.name/demo/camera.php)

Client-side APIs on mobile and desktop devices are quickly providing the same APIs.  Of course our mobile devices got access to some of these APIs first, but those APIs are slowly making their way to the desktop.  One of those APIs is the getUserMedia API, providing developers access to the user's camera.  Let me show you how to get simple camera access from within your browser!

You may also want to see [Image Crop Demo](http://jsfiddle.net/alexk111/rw6q9/)

<a href="../../demo/cameraDemo.html" class="demo" target="_blank">View Demo</a>

The HTML
--------

Please read my note about the HTML structure below:

```
<!--
	Ideally these elements aren't created until it's confirmed that the 
	client supports video/camera, but for the sake of illustrating the 
	elements involved, they are created with markup (not JavaScript)
-->
<video id="video" width="640" height="480" autoplay></video>
<button id="snap">Snap Photo</button>
<canvas id="canvas" width="640" height="480"></canvas>


```

Each of these elements should be created once confirmation of camera support is confirmed, but for the sake of this tutorial, I wanted to show you what the elements look like with basic HTML.  Do note that the dimensions we're working with are 640x480.

The JavaScript
--------------

Since the HTML elements above are already created, the JavaScript portion will look smaller than you think:

```
// Grab elements, create settings, etc.
var video = document.getElementById('video');

// Get access to the camera!
if(navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
    // Not adding `{ audio: true }` since we only want video now
    navigator.mediaDevices.getUserMedia({ video: true }).then(function(stream) {
        //video.src = window.URL.createObjectURL(stream);
        video.srcObject = stream;
        video.play();
    });
}

/* Legacy code below: getUserMedia 
else if(navigator.getUserMedia) { // Standard
    navigator.getUserMedia({ video: true }, function(stream) {
        video.src = stream;
        video.play();
    }, errBack);
} else if(navigator.webkitGetUserMedia) { // WebKit-prefixed
    navigator.webkitGetUserMedia({ video: true }, function(stream){
        video.src = window.webkitURL.createObjectURL(stream);
        video.play();
    }, errBack);
} else if(navigator.mozGetUserMedia) { // Mozilla-prefixed
    navigator.mozGetUserMedia({ video: true }, function(stream){
        video.srcObject = stream;
        video.play();
    }, errBack);
}
*/


```

Once it's been established that the browser supports `navigator.mediaDevices.getUserMedia`, a simple method sets the `video` element's `src` to the user's live camera/webcam.  Calling the `play` method of the video then starts the element's live streaming video connection.  That's all that's required to connect your camera to the browser!

Taking a photo is only marginally more difficult.  Simply add a click listener to a generic button and and draw an image from video!

```
// Elements for taking the snapshot
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');
var video = document.getElementById('video');

// Trigger photo take
document.getElementById("snap").addEventListener("click", function() {
	context.drawImage(video, 0, 0, 640, 480);
});


```

Of course you could add some sexy image filters and make a billion dollars...but I'll save that for another post.  At minimum you could convert the [canvas snapshot to an image](https://davidwalsh.name/convert-canvas-image) though!  I'll talk about canvas image filters in the future...

Being able to access the camera within the browser without using third party software is an incredible advancement.  Paired with canvas and a bit of JavaScript, the camera has become quickly and easily accessible.  Not only it the camera accessible, but since canvas is ultra-flexible, we'll be able to add sexy Instagram-style image filters in the future.  For now, however, simply accessing the camera in our browser moves us miles ahead.  Have fun taking images within your browser!

_Post inspired by [I see you getUserMedia](http://tagsoup.github.com/blog/2012/03/09/i-see-you-getusermedia/); provided a great starting point for this post._

 [![](https://davidwalsh.name/demo/gofast-long.svg)](https://requestmetrics.com/) 

 [![](https://davidwalsh.name/demo/gofast-block.svg)](https://requestmetrics.com/)