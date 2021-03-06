# Universal Analytics for Python

This library provides a Python interface for the Universal Analytics Measurement Protocol, with an interface modeled (loosely) after Google's `analytics.js`.

# Usage

For the most accurate data in your reports, Analytics Pros recommends establishing a distinct ID for each of your users, and integrating that ID on your front-end web tracking, as well as back-end tracking calls. This provides for a consistent, correct representation of user engagement, without skewing overall visit metrics (and others).

A simple example:

```python
from UniversalAnalytics import Tracker

tracker = Tracker.create('UA-XXXXX-Y', client_id = CUSTOMER_UNIQUE_ID)
tracker.send('event', 'Subscription', 'billing')
```

Please see the [test.py](./test.py) script for additional examples.

This library support the following tracking types, with corresponding (optional) arguments:

* pageview: [ page path ]
* event: category, action, [ label [, value ] ] 
* social: network, action [, target ] 
* timing: category, variable, time [, label ]

Additional tracking types supported with property dictionaries:

* transaction
* item
* appview
* exception

Property dictionaries permit the same naming conventions given in the [analytics.js Field Reference](https://developers.google.com/analytics/devguides/collection/analyticsjs/field-reference), with the addition of common spelling variations, abbreviations, and hyphenated names (rather than camel-case).  These are also demonstrated in the [test.py](./test.py) file.

Further, the property dictionaries support names as per the [Measurement Protocol Parameter Reference](https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters), and properties/parameters can be passed as named arguments.

Example:

```python
  # as python named-arguments
  tracker.send('pageview', path = "/test", title = "Test page") 
  
  # as property dictionary 
  tracker.send('pageview', {
    'path': "/test",
    'title': "Test page"
  })
```

# Features not implemented

* Throttling

# License

universal-analytics-python is licensed under the [BSD license](./LICENSE)
