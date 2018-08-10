# react-native-qrcode
A react-native component to generate [QRcode](http://en.wikipedia.org/wiki/QR_code), not only support English.

## Installation
```sh
npm install react-native-qrcode --save
```
## Usage
```jsx
'use strict';

import React, { Component } from 'react'
import QRCode from 'react-native-qrcode';

import {
    AppRegistry,
    StyleSheet,
    View,
    TextInput
} from 'react-native';

class HelloWorld extends Component {
  state = {
    text: 'http://facebook.github.io/react-native/',
  };

  render() {
    return (
      <View style={styles.container}>
        <TextInput
          style={styles.input}
          onChangeText={(text) => this.setState({text: text})}
          value={this.state.text}
        />
        <QRCode
          value={this.state.text}
          size={200}
          bgColor='purple'
          fgColor='white'/>
      </View>
    );
  };
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        backgroundColor: 'white',
        alignItems: 'center',
        justifyContent: 'center'
    },

    input: {
        height: 40,
        borderColor: 'gray',
        borderWidth: 1,
        margin: 10,
        borderRadius: 5,
        padding: 5,
    }
});

AppRegistry.registerComponent('HelloWorld', () => HelloWorld);

module.exports = HelloWorld;
```
## Available Props

prop      | type                 | default value
----------|----------------------|--------------
`value`   | `string`             | `http://facebook.github.io/react-native/`
`size`    | `number`             | `128`
`bgColor` | `string` (CSS color) | `"#000"`
`fgColor` | `string` (CSS color) | `"#FFF"`

<img src='qrcode.png' height = '256' width = '256'/>

## Snapshot Testing

If you use [Jest snapshots](https://jestjs.io/docs/en/tutorial-react-native.html) to test your components, you may have run into 

```javascript
  ● Test suite failed to run

    TypeError: Cannot read property 'decelerationRate' of undefined
```

`react-native-qrcode` relies on some native code. To skip using the native code and continue testing your components, mock `react-native-qrcode`.

```javascript
//testSetup.js

jest.mock('react-native-qrcode', () => 'QRCode')
```

```javascript
// MyQRCodeComponent.test.js

import React from 'react'
import ShallowRenderer from 'react-test-renderer/shallow'

import MyQRCodeComponent from './MyQRCodeComponent.js'

describe('QRCode', () => {
  it('should render', () => {
    const renderer = new ShallowRenderer()
    const actual = renderer.render(<MyQRCodeComponent />)

    expect(actual).toMatchSnapshot()
  })
})

```

# Licenses

All source code is licensed under the [MIT License](https://github.com/cssivision/react-native-qrcode/blob/master/LICENSE).
