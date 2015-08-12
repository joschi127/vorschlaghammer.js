# vorschlaghammer.js

Nice and lightweight alternative to hammer.js. Does not prevent native scrolling e.g. with `overflow: auto;`.

Based on the touch.js Gist by Vitaly Rotari, which is a ported version of the QuoJS touch gestures code which was originally implemented by Javi Jiménez Villar.

Adds support for the following gesture events to jQuery: (based on the very good implementation from QuoJS)

* singleTap
* doubleTap
* hold
* swipe
* swiping
* swipeLeft
* swipeRight
* swipeUp
* swipeDown
* rotate
* rotating
* rotateLeft
* rotateRight
* pinch
* pinching
* pinchIn
* pinchOut
* drag
* dragLeft
* dragRight
* dragUp
* dragDown

Example for "pinching":

    $(document).ready(function() {
        var currentZoom = 1;
        var pinchStartZoom = null;
        $('.some-class').on('touchstart', function (evt, params) {
            pinchStartZoom = currentZoom;
        });
        $('.some-class').on('pinching', function (evt, params) {
            var scale = ($(window).height() + params.distance) / $(window).height();
            currentZoom = pinchStartZoom * scale;
            console.log("currentZoom: ", currentZoom);
        });
    });

Use all other events with .on() in a similar way.
