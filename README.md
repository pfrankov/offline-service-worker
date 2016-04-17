# Magic Cache

Tiny lib with _zero_ dependencies that can handle all `GET` requests, store them in Browser's Cache and return them back in case of connection issues (Offline, DNS Errors).

<img src="https://cloud.githubusercontent.com/assets/584632/14588020/b89c2e6e-04e0-11e6-904d-91b7cc538030.gif" height="500"/>

[This example](https://rawgit.com/pfrankov/magic-cache/master/example/example.html)

## Limitations
Cache API is available over *HTTPS* only. Time to switch to HTTPS!  
Chrome 40+ / Firefox 44+ / Opera 24+ / Chrome for Android 49+  
Working on _Service Workers_ still in progress. _For now_ there can be only one _Service Worker_. It should be changed in near future.  
So if you use SW already - you will not be able to use the MagicCache.

## Installation

```bash
npm install --save git://github.com/pfrankov/magic-cache
# or
git clone https://github.com/pfrankov/magic-cache
```
Then just copy `magic-cache-service-worker.js` to the root directory of your site.


## Usage

### Methods

#### `onCached(callback)`

Subscribe to an event when any request has gotten from the *cache*.
Additionally executed if the current status is _Cached_

```js
var cancelHandler = MagicCache.onCached(function(){
   console.log("Looks like you offline, but don't worry -- you are still geting cached pages"); 
});

// cancelHandler(); to obviously cancel the handler
```

#### `onOnline(callback)`

Subscribe to an event when any request has gotten from *server*.
Additionally executed if the current status is _Online_ 

```js
var cancelHandler = MagicCache.onOnline(function(){
   console.log("Online"); 
});

// cancelHandler(); to obviously cancel the handler 
```

### Attributes

#### `isCached`

`Boolean`. Helps to understand what's going on.

```js
if (MagicCache.isCached) {
    alert("Oh, no!");
}
```