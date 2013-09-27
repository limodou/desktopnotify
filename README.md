desktopnotify
===============

desktopnotify is a js lib, which can use browser notification API to show
notifications. It's developed by limodou, and inspired by https://github.com/gotardo/HTML5-Desktop-Notif
It releases under MIT.

## Installation

```
<script src="desktopnotify.js"></script>
```

## Usage

### Enable notification

html code

```
<a href='#' id="enable">Click to request permission of notification</a>
```

javascript code

```
$('#enable').click(function(){
    Notify.request();
});
```

### Show message

html code

```
<a href='#' id="show">Show</a>
```

javascript code

```
Notify.icon = "/examples/success.ico";
$('#show').click(function(){
    Notify.show({title:'Hello', message:'Test', onclick:function(){
        alert('click');
    }});
});
```

You can also give 'icon' to show function, just like:

```
Notify.show({title:'Hello', message:'Test', icon:"/examples/success.ico"});
```

## Test

You should test it in a web server, so the simple way is: change to desktopnotify
folder, and run:

```
python -m SimpleHTTPServer 8000
```

It'll start an web server. And you can visit: http://localhost:8000/examples/index.html

## Support

Now this lib supports: chrome, firefox, safari

## API

### options

* `icon` default icon
* `title` default title
* `message` default message
* `autoclose` if set, the notification will be closed after n seconds

### methods

* `isSupported()` will return notification factory object, e.g. `window.webkitNotifications`
* `request()` will request permission of notification, and you should bind with click or
  keypress event, call it directly will no use.
* `check()` will return the result of  `window.webkitNotifications.checkPermission()`, the result
  will be:

    * 0 Allowed
    * 1 Not Allowed
    * 2 Denied

* `show(options)` display an message. options will be:

    * `icon` icon of notification, .ico will be the best I think
    * `title`
    * `message`
    * `onshow` callback when show the notification
    * `onclick` callback when click on the notification
    * `onerror` callback when error
    * `onclose` callback when close the notification, in some browser like chrome will not fire this event.

## Other similar projects

* https://github.com/gotardo/HTML5-Desktop-Notif
* https://github.com/ttsvetko/HTML5-Desktop-Notifications