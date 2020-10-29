# uuid-list

list of unique id implementations, design considerations, and resources. may also overlap somewhat with the topic of hashing

## Desirable Properties

- extremely low chance of collision
- chronologically sortable
- alphabetically sortable? (k-sortable?)
- 64 bits (instead of 128bits) or otherwise fixed length (bc of storage concerns)
- inputs:
  - timestamp
  - string?
- no dependencies
- no need for coordination (among different clients generating uuid's)
  
## Concepts

- https://en.wikipedia.org/wiki/Universally_unique_identifier
- RFC: A Universally Unique IDentifier (UUID) URN Namespace - https://tools.ietf.org/html/rfc4122
- k-sorting http://ci.nii.ac.jp/naid/110002673489/

    > We’re aiming to keep our k below 1 second, meaning that tweets posted within a second of one another will be within a second of one another in the id space too.

- KSUID's https://github.com/segmentio/ksuid (segment)
- ulid's https://github.com/ulid/spec ([instagram](http://instagram-engineering.tumblr.com/post/10853187575/sharding-ids-at-instagram), [firebase](https://firebase.googleblog.com/2015/02/the-2120-ways-to-ensure-unique_68.html))
- c4 ID's http://www.cccc.io/

## Impls

grab n go: https://www.uuidgenerator.net/

super simple dumb unique id

```js
function id () {
  return Math.random().toString(36).substring(2) + Date.now().toString(36);
}
```

better uuid?

```js
https://www.w3resource.com/javascript-exercises/javascript-math-exercise-23.php
export function uuid() {
  var dt = new Date().getTime()
  var uuid = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(
    c
  ) {
    var r = (dt + Math.random() * 16) % 16 | 0
    dt = Math.floor(dt / 16)
    // eslint-disable-next-line
    return (c == 'x' ? r : (r & 0x3) | 0x8).toString(16)
  })
  return uuid
}
```


- Twitter Snowflake (2010-2014) https://blog.twitter.com/engineering/en_us/a/2010/announcing-snowflake.html
- fast random ID: https://github.com/lukeed/uid
- uuid/v4
  - https://digitalbunker.dev/2020/09/30/understanding-how-uuids-are-generated/
  - https://github.com/lukeed/uuid
  - https://github.com/uuidjs/uuid
