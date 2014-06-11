BlendMicro npm
==============
Node.js module for [BlendMicro](http://redbearlab.com/blendmicro/) with BLE.

    Node.js <---(BLE)---> BlendMicro

- using [noble npm](http://npmjs.org/package/noble) as BLE wrapper
- [serialport npm](https://www.npmjs.org/package/serialport) like API

sites

- https://www.npmjs.org/package/blendmicro
- https://github.com/shokai/blendmicro-node


Install
-------

    % npm install blendmicro


Samples
-------

see [samples](https://github.com/shokai/blendmicro-node/tree/master/samples) directory.


Usage
-----

### Open

blendmicro side

```c
#include <SPI.h>
#include <boards.h>
#include <RBL_nRF8001.h>

void setup(){
  ble_set_name("BlendMicro");
  ble_begin();
}
```

node.js side

```javascript
var BlendMicro = require('blendmicro');

// search device with BLE peripheral name
var bm = new BlendMicro("BlendMicro");

// search with deefault name "BlendMicro"
var bm = new BlendMicro();
```


### Read/Write

```javascript
bm.on('open', function(){
  console.log("open!!");

  // read data
  bm.on("data", function(data){
    console.log(data.toString());
  });

  // write data
  setInterval(function(){
    bm.write("hello");
  });

});
```

### Close

```javascript
bm.close(function(){
  console.log("closed");
});
```


Contributing
------------
1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
