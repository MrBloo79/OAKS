Inline task annotations
__
```
value
```
__
```js
return "[⭐:: ]";
```
__
__
```
requester
```
__
```js
return "[💬:: ]";
```
__
__
```
assignee
```
__
```js
return "[👤:: ]";
```
__
__
```
more
```
__
```js
return "[🔗:: ]";
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
// Unique ID with low collision probability from https://github.com/ai/nanoid
const POOL_SIZE_MULTIPLIER = 128
let pool, poolOffset

function fillPool(bytes) {
  if (!pool || pool.length < bytes) {
    pool = Buffer.allocUnsafe(bytes * POOL_SIZE_MULTIPLIER)
    crypto.getRandomValues(pool)
    poolOffset = 0
  } else if (poolOffset + bytes > pool.length) {
    crypto.getRandomValues(pool)
    poolOffset = 0
  }
  poolOffset += bytes
}

function random(bytes) {
  fillPool((bytes -= 0))
  return pool.subarray(poolOffset - bytes, poolOffset)
}

function customRandom(alphabet, defaultSize, getRandom) {
  let mask = (2 << (31 - Math.clz32((alphabet.length - 1) | 1))) - 1
  let step = Math.ceil((1.6 * mask * defaultSize) / alphabet.length)

  return (size = defaultSize) => {
    let id = ''
    while (true) {
      let bytes = getRandom(step)

      let i = step
      while (i--) {
        id += alphabet[bytes[i] & mask] || ''
        if (id.length === size) return id
      }
    }
  }
}

function customAlphabet(alphabet, size = 21) {
  return customRandom(alphabet, size, random)
}

const nanoid = customAlphabet('0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz', 9)

return `^${nanoid()}`;
```
__