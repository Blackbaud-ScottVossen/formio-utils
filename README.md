# formio-utils
Utility functions for form.io

## Installing

```
$ npm install formio-utils
```

## Functions

### eachComponent(components, fn, includeAll, path)

Calls `fn(component)` for each component in `components`, accounting for nested layout components. (Does not call for layout components themselves, unless includeAll is true).

The current data path of the element. Example: data.user.firstName

```javascript
var utils = require('formio-utils');

utils.eachComponent(form.components, function(component) {
	// Do something...
})
```

### getComponent(components, key)

Returns the component with the given `key` or undefined if not found.

```javascript
var utils = require('formio-utils');

var component = utils.getComponent(form.components, 'myKey');
```

### flattenComponents(components, includeAll)

Returns an key-value object where the keys are the keys for each component in `components` and each key points to the corresponding component. This includes nested components as well. Pass true for includeAll if you want to include layout components.

```javascript
var utils = require('formio-utils');

var flattened = utils.flattenComponents(form.components);
console.log(flattened['myNestedComponent']);
```

### isLayoutComponent(component)

Determine if a component is a layout component.

```javascript
var utils = require('formio-utils');

var layoutComponent = utils.isLayoutComponent(form.components[0]);
console.log(layoutComponent);
```

### getValue(submission, componentKey)

Get the value for a components API key, from the given submission. Recursively searches the submission for the key.

```javascript
var utils = require('formio-utils');

var value = utils.getValue(submission, 'myComponent'); // The value or undefined.
```

## Testing

```
$ npm run test
```