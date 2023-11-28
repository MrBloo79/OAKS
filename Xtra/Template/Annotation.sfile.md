Inline task annotations
__
```
rank
```
__
```js
return "[🏅:: ]";
```
__
__
```
requester
```
__
```js
return "[💬:: [[]";
```
__
__
```
assignee
```
__
```js
return "[👤:: [[]";
```
__
__
```
details
```
__
```js
return "[ℹ️:: [[]";
```
__
__
```
created
```
__
```js
return '➕ @';
```
__
__
```
scheduled
```
__
```js
return '⏳ @';
```
__
__
```
due
```
__
```js
return '📅 @';
```
__
__
```
blockId
```
__
```js
// Unique ID with low collision probability: https://github.com/ai/nanoid
const nanoid=crypto.getRandomValues(new Uint8Array(11)).reduce(((t,e)=>t+=(e&=63)<36?e.toString(36):e<62?(e-26).toString(36).toUpperCase():e>62?"-":"_"),"");

return ` ^${nanoid}`;
```
__