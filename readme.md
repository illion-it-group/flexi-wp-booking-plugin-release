# Flexi Booking WordPress Plugin

---
> This is a public release repository and contains only the releases of the [flexi-wp-booking-plugin](https://github.com/illion-it-group/flexi-wp-booking-plugin) repository
---

## Requirements
- PHP ^7.4
- WordPress ^6.0.0
- [flexi-wp-mu-plugins](https://bitbucket.org/illionitgroup/flexi-wp-mu-plugins/src/main/) ^1.1
- Public-Api credentials

## Installation & Setup
- Install the `flexi-wp-mu-plugins` MU plugin
- Install and enable __this__ plugin
- Go to the settings page: WP Admin / Flexi Booking
- Enter your Public-Api credentials and save it.
> If the credentials disappear the setup was successful.
- Create your first Widget: WP Admin / Booking Widgets
- Embed your widget via shortcodes or a WP Widget _(Flexi Booking)_

## Shortcodes examples
```
[flexi-booking id="1"]
[flexi-booking id="1" language="en"]
[flexi-booking id="1" language="en" iframe=1]
[flexi-booking id="1" language="en" iframe=1 width="1200px" height="900px"]
```
> Use the `iframe` attribute if you experience any issues

## Dynamic localization
By default, the rendered widgets have a static language set to them.

You can override this dynamically from anywhere using the following filter:
```php
add_filter(
    'flexi_booking_widget_language', # The name of the hook
    function(string $language, int $widgetId) {
        return 'en_GB'; # Here you can return any language code
    },
    10, # Priority in the WP hook order
    2   # The number of arguments
);
```

## Rendering programmatically
To render the Booking widget via PHP code we can use the following commands:
```php
print FlexiBookingManager::renderWidget(1, 'en');
```

For `iframe` rendering we can use the following command:
```php
print FlexiBookingManager::renderWidgetIframe(1, 'en', '800px', '400px');
```

Alternatively we can use the WP shortcode functionality as well:
```php
print do_shortcode('[flexi-booking id="1" language="en"]');
```