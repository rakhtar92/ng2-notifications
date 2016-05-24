# Angular 2 System Notifications

[![](./src/public/img/demo.gif)]()

> The Notifications API allows web pages to control the display of system notifications to the end user — these are outside the top-level browsing context viewport, so therefore can be displayed even the user has switched tabs or moved to a different app. The API is designed to be compatible with existing notification systems across different platforms.

[Read More about the API](https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API)

[Read the blog post](https://medium.com/@castillo.io/native-web-push-notifications-with-angular-2-c774a72c009e)

## Demo

[Launch Demo](http://embed.plnkr.co/cHFcMsvL8lGX9Pnm4UVl/)

## Quick Start

```bash
$ npm install ng2-notifications --save
```

Then add it to your app:

``` ts
import { SystemNotificationDirective } from 'ng2-notifications';

@Component({
  selector: 'my-app',
  template: `
  <systemNotification 
    title="ng2-notifications"
    body="Directive for Native System Notifications"
    icon="https://goo.gl/3eqeiE">
  </systemNotification>
  `,
  directives: [SystemNotificationDirective]
})
```

## Usage

Example of a basic notification using literals for title, description and icon.
Please note this notification will not close by itself.

``` html
<systemNotification 
  title="ng2-notifications"
  body="Directive for Native System Notifications"
  icon="https://goo.gl/3eqeiE">
</systemNotification>
```

For data binding use:

``` html
<systemNotification 
  [title]="notification.title"
  [body]="notification.description"
  [icon]="notification.icon">
</systemNotification>
```

### Self-closing

To self-close after a period of time, just add the `[closeDelay]` attribute with a value of milliseconds. The example below will self-close in 5 seconds.

``` html
<systemNotification 
  ...
  closeDelay="5000">
</systemNotification>
```

### Controlling when to fire a notification

It is possible to control when a notification is shown. 
Simply bind a boolean expression to the `[when]` attribute.

``` html
<systemNotification 
  ...
  [when]="booleanExpression">
</systemNotification>
```

### Click Event

To attach a click handler to a notification, add the `(onClick)` event.

``` html
<systemNotification 
  ...
  (onClick)="myFunction($event)">
</systemNotification>
```

### Show and Close events

It is possible to listen for show/close events to fire and attach a callback.

``` html
<systemNotification 
  ...
  (onShow)="myShowFunction($event)"
  (onClose)="mycloseFunction($event)">
</systemNotification>
```

### Error Event

This event is unlikely, but in order to attach a callback to the notification error event, simply use the `(onError)` event.

``` html
<systemNotification 
  ...
  (onError)="handleError($event)">
</systemNotification>
```

## Other Options

* data
* tag
* dir: (default: 'auto')
* lang: (default: 'en-US')

## Browser Support

[See Browser Support](http://caniuse.com/#feat=notifications)

The folowing options are either in recommendation state or have no browser support currently.

* [Renotify](https://developer.mozilla.org/en-US/docs/Web/API/notification/renotify)
* [Silent](https://developer.mozilla.org/en-US/docs/Web/API/notification/silent)
* [Sound](https://developer.mozilla.org/en-US/docs/Web/API/notification/silent)
* [Vibrate](https://developer.mozilla.org/en-US/docs/Web/API/notification/vibrate)
* [Sticky](https://developer.mozilla.org/en-US/docs/Web/API/notification/sticky)
* [Noscreen](https://developer.mozilla.org/en-US/docs/Web/API/notification/noscreen)

It is important to know if you’re browsing in incognito mode in Google Chrome, you won’t get notifications.

## License

The MIT License ([MIT](/LICENSE))

Copyright (c) 2016 Alex Castillo

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
