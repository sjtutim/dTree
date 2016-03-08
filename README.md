# dTree
*A library for visualizing data trees with multiple parents built on top of D3.*

[![npm](https://img.shields.io/npm/v/d3-dtree.svg)](https://www.npmjs.com/package/d3-dtree) [![Bower](https://img.shields.io/bower/v/d3-dtree.svg)](https://github.com/ErikGartner/dTree) [![Dependency Status](https://david-dm.org/ErikGartner/dtree.svg)](https://david-dm.org/ErikGartner/dtree) [![devDependency Status](https://david-dm.org/ErikGartner/dtree/dev-status.svg)](https://david-dm.org/ErikGartner/dtree#info=devDependencies)

## Treehouse
There exists a playground/open repository for dTree graphs called [Treehouse](https://treehouse.gartner.io). There anyone can host a dTree graph without having to create a website or interact directly with the library.

Checkout **the demo graph** for dTree:
https://treehouse.gartner.io/t/dtree-demo

## Installation
There are several ways to use dTree. One way is to simply include the compiled file ```dTree.js``` that then exposes a ```dTree``` variable. dTree is available on both NPM and Bower as *d3-dtree*.

Lastly dTree is also available through the RawGit CDN:
```
https://cdn.rawgit.com/ErikGartner/dTree/1.3.1/dist/dTree.min.js
```

## Requirements
To use the library the follow dependencies must be loaded:

 - [D3](https://github.com/mbostock/d3) v3.x
 - [lodash](https://github.com/lodash/lodash) v4.x

## Usage
To create a graph from data use the following command:
```javascript
dTree.init(data, options);
```

The data object should have the following structure:
```javascript
[{
  name: "Father",
  class: "overriding-css-class",
  textClass: "overriding-css-class",
  depthOffset: 1,
  marriages: [{
    spouse: {
      name: "Mother",
      class: "overriding-css-class"
    },
    children: [{
      name: "Child",
      class: "child-class"
    }]
  }],
  extra: {}
}]
```

The options object has the following default values:
```javascript
{
  target: '#graph',
  debug: false,
  width: 600,
  height: 600,
  callbacks: {
    nodeClick: function(name, extra, id) {},
    nodeRenderer: function(name, x, y, height, width, extra, id, nodeClass, textClass, textRenderer) {
      return TreeBuilder._nodeRenderer(name, x, y, height, width, extra,
        id, nodeClass, textClass, textRenderer);
    },
    nodeSize: function(nodes, width, textRenderer) {
      // Should set cHeight and cWidth for each node and return the maxima.
      return TreeBuilder._nodeSize(nodes, width, textRenderer);
    },
    nodeSorter: function(aName, aExtra, bName, bExtra) {return 0;},
    textRenderer: function(name, extra, textClass) {
      return TreeBuilder._textRenderer(name, extra, textClass);
    }
  },
  margin: {
    top: 0,
    right: 0,
    bottom: 0,
    left: 0
  },
  nodeWidth: 100,
  styles: {
    node: 'node',
    linage: 'linage',
    marriage: 'marriage',
    text: 'nodeText'
  }
}
```

The following CSS sets some good defaults:
```css
.linage {
    fill: none;
    stroke: black;
}
.marriage {
    fill: none;
    stroke: black;
}
.node {
    background-color: lightblue;
    border-style: solid;
    border-width: 1px;
}
.nodeText{
    font: 10px sans-serif;
}
```

## Development
To setup and build the library from scratch follow these steps:

1. ```npm install --save-dev```
2. ```npm run-script build```

A demo is available by running:
```
gulp demo
```
It hosts a demo on localhost:3000 by serving ```test/demo```.

## Contributions
To make contributions please follow the contributions document.

## License
The MIT License (MIT)

Copyright (c) 2015 Erik Gärtner
