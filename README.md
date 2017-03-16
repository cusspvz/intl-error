# intl-error
react-intl/intl compatible error

Handle better your errors, add intl compatible errors to your webapp actions.

## Installation
```bash
yarn add intl-error
```

## Usage
```javascript
import React, { Component } from 'react'
import IntlError from 'intl-error'
import { injectIntl } from 'react-intl'

function doSomething () {
  throw new IntlError({ id: 'testing' })
}

@injectIntl
export default class TestComponent extends Component {
  state = { error: undefined }

  render () {
    const { state: { error }, props: { intl }, onClick } = this
    return (
      <div onClick={onClick}>
        {error && error.formatMessage(intl)}
       </div>
    )
  }

  onClick = async () => {
    try {
      doSomething()
    } catch (error) {
      await this.setState({ error })
    }
  }
}
 
```
