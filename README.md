
`<request-data-aware>` Element that is aware of the RequestObject currently
loadded into the app.

The element contains the same request object data as other
`<request-data-aware>` elements whenever their location in the document.
The request object is encapsulated in the `scope` attribute.
By default the `scope` is `default`. If you create two `<request-data-aware>`s
with different scopes then changing one request object will not affect
the other.

Setting a request data on a `<request-data-aware>` will notify other awares
with the same scope about the change and update their request data so it can
be transfered between different parts of application on even different
web components.

### Example
```html
<request-data-aware request="{{request}}" scope="request"></request-data-aware>
<request-data-aware request="{{importRequest}}" scope="import"></request-data-aware>
<request-data-aware scope="request" id="receiver"></request-data-aware>
```
```javascript
var a1 = document.querySelector('request-data-aware[scope="request"]');
var a2 = document.querySelector('request-data-aware[scope="import"]');
var a3 = document.querySelector('#receiver');
r1.request = {};
r2.request = null;
assert(r1.request !== a2.request);
assert(r1.request === a3.request);
```

