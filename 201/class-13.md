# Read: 13 - Local Storage

## The Past, Present, and Future of Local Storage for Web Applications

### INTRODUCING HTML5 STORAGE

- the problem that HTML5 set out to solve: to provide a standardized API, implemented natively and consistently in multiple browsers, without having to rely on third-party plugins.
- So what is HTML5 Storage? Simply put, it’s a way for web pages to store named key/value pairs locally, within the client web browser.
- From your JavaScript code, you’ll access HTML5 Storage through the localStorage object on the global window object.
- check for HTML5 storage
```
function supports_html5_storage() {
  try {
    return 'localStorage' in window && window['localStorage'] !== null;
  } catch (e) {
    return false;
  }
}
```
- Instead of writing this function yourself, you can use Modernizr to detect support for HTML5 Storage.
```
if (Modernizr.localstorage) {
  // window.localStorage is available!
} else {
  // no native support for HTML5 storage :(
  // maybe try dojox.storage or a third-party solution
}
```


### USING HTML5 STORAGE

- HTML5 Storage is based on named key/value pairs.
- You store data based on a named key, then you can retrieve that data with the same key.
```
interface Storage {
  getter any getItem(in DOMString key);
  setter creator void setItem(in DOMString key, in any data);
};
```
- Calling setItem() with a named key that already exists will silently overwrite the previous value.
- Like other JavaScript objects, you can treat the localStorage object as an associative array. Instead of using the getItem() and setItem() methods, you can simply use square brackets. For example
```
var foo = localStorage.getItem("bar");
// ...
localStorage.setItem("bar", foo);
```
- or
```
var foo = localStorage["bar"];
// ...
localStorage["bar"] = foo;
```
- There are also methods for removing the value for a given named key, and clearing the entire storage area (that is, deleting all the keys and values at once).
```
interface Storage {
  deleter void removeItem(in DOMString key);
  void clear();
};
```
- Calling removeItem() with a non-existent key will do nothing.
- Finally, there is a property to get the total number of values in the storage area, and to iterate through all of the keys by index (to get the name of each key).
```
interface Storage {
  readonly attribute unsigned long length;
  getter DOMString key(in unsigned long index);
};
```
- If you call key() with an index that is not between 0–(length-1), the function will return null.

### TRACKING CHANGES TO THE HTML5 STORAGE AREA

- The storage event is fired on the window object whenever **setItem(), removeItem(), or clear() is called and actually changes something.**
- The storage event is supported everywhere the localStorage object is supported,
- to hook the storage event, you’ll need to check which event mechanism the browser supports.
-```
if (window.addEventListener) {
  window.addEventListener("storage", handle_storage, false);
} else {
  window.attachEvent("onstorage", handle_storage);
};

```
```
- The handle_storage callback function will be called with a StorageEvent object,**except in Internet Explorer where the event object is stored in window.event.**
```
function handle_storage(e) {
  if (!e) { e = window.event; }
}
```

### STORAGEEVENT OBJECT

```
PROPERTY	TYPE	DESCRIPTION
key	string	the named key that was added, removed, or modified
oldValue	any	the previous value (now overwritten), or null if a new item was added
newValue	any	the new value, or null if an item was removed
url*	string	the page which called a method that triggered this change
* Note: the url property was originally called uri. Some browsers shipped with that property before the specification changed. For maximum compatibility, you should check whether the url property exists, and if not, check for the uri property instead.
```
- The storage event is not cancelable. From within the handle_storage callback function, there is no way to stop the change from occurring. It’s simply a way for the browser to tell you, “hey, this just happened. There’s nothing you can do about it now; I just wanted to let you know.”

### HTML5 STORAGE IN ACTION

- an example would be a browser game that would usually lose all its data when the page is closed but with HTML% storage you can leave or close the page and come back to it with your game play data saved.

### BEYOND NAMED KEY-VALUE PAIRS: COMPETING VISIONS

- Web SQL Database (formerly known as “WebDB”) provides a thin wrapper around a SQL database, allowing you to do things like this from JavaScript:
 example - actual working code in 4 browsers
 ```
 openDatabase('documents', '1.0', 'Local document storage', 5*1024*1024, function (db) {
  db.changeVersion('', '1.0', function (t) {
    t.executeSql('CREATE TABLE docids (id, name)');
  }, error);
});
```
 - link to article - http://diveinto.html5doctor.com/storage.html

[Back to code 201 notes](../201.md)