# React-Native List Popover

Popover is a great way to show a list of items for users to choose from. With <ListPopover/> component you can add a very simple pop over screen with a list of items as the child component and access the selected item from the parent component. It is a very easy way of adding a list of options to the UI.

The main properties to send from the parent component:
* `list` list of items to choose from, see example for required object keys
* `isVisible` indicator that makes the popover visible or not
* `onClick` callback function that takes an `item` parameter to handle the click operation
* `onClose` callback function to set the isVisible to false to close the popover
* `maxHeightFraction` fraction or decimal, used to change the maxHeight of the list in relation to the window height. Defaults to 3/4 if not set
* `scrollBounce` set to false to disable scroll bouncing on iOS, defaults to true


## Screenshots
Before | List Popover | Selected
-------|--------------|---------
![](https://raw.githubusercontent.com/bulenttastan/react-native-list-popover/master/Screenshots/screen1.png) | ![](https://raw.githubusercontent.com/bulenttastan/react-native-list-popover/master/Screenshots/screen2.png) | ![](https://raw.githubusercontent.com/bulenttastan/react-native-list-popover/master/Screenshots/screen3.png)

# Usage

```js
import React from 'react';
import {StyleSheet, Text, View, TouchableHighlight} from 'react-native';
import ListPopover from 'react-native-list-popover';

const items = [
  {
    'id': 'unique_item_1_id',
    'title': 'Item 1',
  },
  {
    'id': 'unique_item_2_id',
    'title:': 'Item 2',
  }
];

export default class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      isVisible: false
    };
  }

  render() {
    return (
      <View style={styles.container}>
        <TouchableHighlight
          style={styles.button}
          onPress={() => this.setState({isVisible: true})}>
          <Text>{this.state.item || 'Select'}</Text>
        </TouchableHighlight>
        <ListPopover
          list={items}
          isVisible={this.state.isVisible}
          onClick={(item) => this.setState({item: item})}
          onClose={() => this.setState({isVisible: false})}/>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    backgroundColor: '#532860',
    justifyContent: 'center',
  },
  button: {
    backgroundColor: '#b8c',
    borderRadius: 4,
    marginLeft: 10,
    marginRight: 10,
    padding: 10,
  },
});
```
