Layout list component
=====================

[![build status](https://img.shields.io/travis/magsdk/component-layout-list.svg?style=flat-square)](https://travis-ci.org/magsdk/component-layout-list)
[![npm version](https://img.shields.io/npm/v/mag-component-layout-list.svg?style=flat-square)](https://www.npmjs.com/package/mag-component-layout-list)
[![dependencies status](https://img.shields.io/david/magsdk/component-layout-list.svg?style=flat-square)](https://david-dm.org/magsdk/component-layout-list)
[![devDependencies status](https://img.shields.io/david/dev/magsdk/component-layout-list.svg?style=flat-square)](https://david-dm.org/magsdk/component-layout-list?type=dev)
[![Gitter](https://img.shields.io/badge/gitter-join%20chat-blue.svg?style=flat-square)](https://gitter.im/DarkPark/magsdk)


Layout list is a component to build user interface, an instance of [Component](https://github.com/stbsdk/component) module.
It is based on [mag-component-list](https://github.com/magsdk/component-list) and [mag-component-layout](https://github.com/magsdk/component-layout).


## Installation ##

```bash
npm install mag-component-layout-list
```


## Usage ##

Add the singleton to the scope:

```js
var LayoutList = require('mag-component-layout-list');
```

Create layout list instance:

```js
var layoutList = new LayoutList({
    // mag-component-list config
    cycle: false,
    className: 'list',

    data: [
        {
            // mag-component-layout config.data
            items: [
                new Button({value: 'Ok'}),
                new Button({value: 'Cancel'}),
                new Button({value: 'Exit'})
            ]
        },
        {
            // mag-component-layout config.data
            items: [
                HTMLElement1,
                HTMLElement2
            ],
            value: someItemData2
        },
        {
            items: [
                  {
                     className: 'star',
                     name: '$icon'
                  },
                  {
                      value: 'Some text',
                      name: '$text'
                  }
              ],
              click: function () {
                  // do something
              },
              name: 'starItem'
          },
          {
              items: [
                  'Hello world',
                  {
                      value: 'hi',
                      className: 'status'
                  }
              ],
              value:{
                  uri: 'http://55.55.55.55/some'
              },
              click: someHandler
          }
        
    ],

    // custom render function
    render: function ( $item, config ) {},

    noData: 'No items',
    fixedData: true,
    size: 3,
    focusIndex: 0,
    propagate: false,
    type: LayoutList.prototype.TYPE_HORIZONTAL,
    events: {
        'focus:item': function ( event ) {
            console.log(event);
        },
        'click:item': function ( event ) {
            console.log(event);
        }
    }
});

layoutList.links.starItem.links.$text.innerText = 'new cool text';

```

To change data after creation:

```js
layoutList.setData({
    focusIndex: 0,
    data: [
        {
            items: [
                  {
                     className: 'star'
                  },
                  'Some text'
              ],
              click: function () {
                  // do something
              }
          },
          {
              items: [
                  'Hello world',
                  {
                      value: 'hi',
                      className: 'status'
                  }
              ],
              value:{
                  uri: 'http://55.55.55.55/some'
              },
              click: someHandler
          },
          {
              items: [
                  {
                      className: 'big',
                      value: ' Some'
                  },
                  {
                      value: new Input()
                  }
              ]
          }
    ]
});
```

To change focus position:

```js
layoutList.focusIndex(index);
```

## Development mode ##

> There is a global var `DEVELOP` which activates additional consistency checks and protection logic not available in release mode.


## Contribution ##

If you have any problem or suggestion please open an issue [here](https://github.com/magsdk/component-layout-list/issues).
Pull requests are welcomed with respect to the [JavaScript Code Style](https://github.com/DarkPark/jscs).


## License ##

`mag-component-layout-list` is released under the [MIT License](license.md).
