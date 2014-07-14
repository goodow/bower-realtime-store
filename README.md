bower-realtime-store
======================

This repo is for distribution on `bower`. The source for this module is in the
[main realtime-store repo](https://github.com/goodow/realtime-store).
Please file issues and pull requests against that repo.

## Install

Install with `bower`:

```shell
bower install 'realtime-store#gh-pages'
```

Add `<script>` tags to your `index.html`:

```html
<script src="/bower_components/bower-sockjs-client/sockjs.js"></script>
<script src="/bower_components/google-diff-match-patch-js/diff_match_patch.js"></script>
<script src="/bower_components/realtime-store/realtime.store.js"></script>
<script src="/bower_components/realtime-store/realtime.store.databinding.js"></script>
```

## Usage
```javascript
var store = new realtime.store.StoreImpl("http://localhost:1986/channel", null);
var bus = store.getBus();

var onLoadedFn = function(document) {
  var model = document.getModel();
  var root = model.getRoot();
  var name = root.get("name");
  console.log("Name: " + name.getText());
};

var opt_initializerFn = function(model) {
  var name = model.createString("Larry Tin");
  var root = model.getRoot();
  root.set("name", name);
};

store.load("docType/docId", onLoadedFn, opt_initializerFn, null);
```
See a full example at https://github.com/goodow/realtime-web-playground

You can try out the Goodow Realtime Store API Playground on its [live instance](http://realtimeplayground.goodow.com).
