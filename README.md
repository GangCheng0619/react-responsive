# react-responsive [![NPM version][npm-image]][npm-url] [![Downloads][downloads-image]][npm-url] [![Support us][gittip-image]][gittip-url]


## Information

<table>
<tr>
<td>Package</td><td>react-responsive</td>
</tr>
<tr>
<td>Description</td>
<td>Media queries in react for responsive design</td>
</tr>
<tr>
<td>Browser Version</td>
<td>>= IE6*</td>
</tr>
</table>

This module is pretty straightforward: You specify a set of requirements, and the children will be rendered if they are met. Also handles changes so if you resize or flip or whatever it will all be cool.

## Usage

A Mq element functions like any other React component, which means you can nest them and do all the normal jazz.

### Using CSS Media Queries

```jsx
var Mq = require('react-responsive');

var A = React.createClass({
  render: function(){
    return (
      <div>
        <div>Device Test!</div>
        <Mq query='(min-device-width: 1224px)'>
          <div>You are a desktop or laptop</div>
          <Mq query='(min-device-width: 1824px)'>
            <div>You also have a huge screen</div>
          </Mq>
          <Mq query='(max-width: 1224px)'>
            <div>You are sized like a tablet or mobile phone though</div>
          </Mq>
        </Mq>
        <Mq query='(max-device-width: 1224px)'>
          <div>You are a tablet or mobile phone</div>
        </Mq>
        <Mq query='(orientation: portrait)'>
          <div>You are portrait</div>
        </Mq>
         <Mq query='(orientation: landscape)'>
          <div>You are landscape</div>
        </Mq>
        <Mq query='(min-resolution: 2dppx)'>
          <div>You are retina</div>
        </Mq>
      </div>
    );
  }
});
```

### Using Properties

To make things more idiomatic to react, you can use camelcased shorthands to construct media queries.


For a list of all possible shorthands and value types see https://github.com/wearefractal/react-responsive/blob/master/src/mediaQuery.js#L9


Any numbers given as a shorthand will be expanded to px (`1234` will become `'1234px'`)


```jsx
var Mq = require('react-responsive');

var A = React.createClass({
  render: function(){
    return (
      <div>
        <div>Device Test!</div>
        <Mq minDeviceWidth={1224}>
          <div>You are a desktop or laptop</div>
          <Mq minDeviceWidth={1824}>
            <div>You also have a huge screen</div>
          </Mq>
          <Mq maxWidth={1224}>
            <div>You are sized like a tablet or mobile phone though</div>
          </Mq>
        </Mq>
        <Mq maxDeviceWidth={1224}>
          <div>You are a tablet or mobile phone</div>
        </Mq>
        <Mq orientation='portrait'>
          <div>You are portrait</div>
        </Mq>
         <Mq orientation='landscape'>
          <div>You are landscape</div>
        </Mq>
        <Mq minResolution='2dppx'>
          <div>You are retina</div>
        </Mq>
      </div>
    );
  }
});
```

### Server rendering

Server rendering can be done by passing static values through the `values` property.

The values property can contain `orientation`, `scan`, `aspectRatio`, `deviceAspectRatio`,
`height`, `deviceHeight`, `width`, `deviceWidth`, `color`, `colorIndex`, `monochrome`,
and `resolution` to be matched against the media query.

```jsx
var Mq = require('react-responsive');

var A = React.createClass({
  render: function(){
    return (
      <div>
        <div>Device Test!</div>
        <Mq minDeviceWidth={1224} values={{deviceWidth: 1600}}>
          <div>You are a desktop or laptop</div>
          <Mq minDeviceWidth={1824}>
            <div>You also have a huge screen</div>
          </Mq>
          <Mq maxWidth={1224}>
            <div>You are sized like a tablet or mobile phone though</div>
          </Mq>
        </Mq>
        <Mq maxDeviceWidth={1224}>
          <div>You are a tablet or mobile phone</div>
        </Mq>
        <Mq orientation='portrait'>
          <div>You are portrait</div>
        </Mq>
         <Mq orientation='landscape'>
          <div>You are landscape</div>
        </Mq>
        <Mq minResolution='2dppx'>
          <div>You are retina</div>
        </Mq>
      </div>
    );
  }
});
```

## Browser Support

### Out of the box

<table>
<tr>
<td>Chrome</td>
<td>9</td>
</tr>
<tr>
<td>Firefox (Gecko)</td>
<td>6</td>
</tr>
<tr>
<td>Internet Explorer</td>
<td>10</td>
</tr>
<tr>
<td>Opera</td>
<td>12.1</td>
</tr>
<tr>
<td>Safari</td>
<td>5.1</td>
</tr>
</table>

### With Polyfills

Pretty much everything. Check out these polyfills:

- [matchMedia.js by Paul Irish](https://github.com/paulirish/matchMedia.js/)
- [media-match (faster, but larger and lacking some features)](https://github.com/weblinc/media-match)

[gittip-url]: https://www.gittip.com/WeAreFractal/
[gittip-image]: http://img.shields.io/gittip/WeAreFractal.svg

[downloads-image]: http://img.shields.io/npm/dm/react-responsive.svg
[npm-url]: https://npmjs.org/package/react-responsive
[npm-image]: http://img.shields.io/npm/v/react-responsive.svg
