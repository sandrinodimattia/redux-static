# Redux Static

Static initialization for Redux. This allows you to define your actions and state in the same way that you define `propTypes` and `defaultProps`.

Example:

```js
import { connectContainer } from 'redux-static';
import React, { Component, PropTypes } from 'react';

import { invoiceActions } from '../actions';

export default connectContainer(class extends Component {
  static stateToProps = (state) => ({
    invoices: state.invoices
  });

  static actionsToProps = {
    ...invoiceActions
  }

  static propTypes = {
    configuration: PropTypes.object,
    saveConfiguration: PropTypes.func.required,
    fetchConfiguration: PropTypes.func.required
  }

  componentWillMount() {
    this.props.fetchConfiguration();
  }

  render() {
    return <InvoicesTable invoices={invoices} />;
  }
});
```

## License

MIT
