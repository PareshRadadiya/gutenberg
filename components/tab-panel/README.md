TabPanel
=======

TabPanel is a React component to render an ARIA-compliant TabPanel. It has two sections: a list of tabs, and the view to show when tabs are chosen. When the list of tabs gets focused, the active tab gets focus (the first tab if there isn't one already). Using the arrow keys navigate between tabs AND select the newly focused tab at the same time.

TabPanel's children are rendered using Function as a Child Component. The function is the tabName as an argument.

## Usage

Renders a TabPanel with each tab representing a paragraph with its title.

```jsx

import { TabPanel } from '@wordpress/components';

const chooseTab = ( tabName ) => {
	console.log( 'Choosing tab', tabName );
};

function MyTabPanel() {
	return (
		<TabPanel className="my-tab-panel"
			activeClass="active-tab"
			tabs={ [
				{
					name: 'tab1',
					title: 'Tab 1',
					className: 'tab-one',
					onSelect: this.chooseTab,
				},
				{
					name: 'tab2',
					title: 'Tab 2',
					className: 'tab-two',
					onSelect: this.chooseTab,
				},
			] }>
			{
				( tabKey ) => {
					return <p>${ tabKey }</p>;
				}
			}
		</TabPanel>
	)
}
```

## Props

The component accepts the following props:

### className

The class to give to the outer container for the TabPanel

- Type: `String`
- Required: No
- Default: ''

### orientation

The orientation of the tablist (`vertical` or `horizontal`)

- Type: `String`
- Required: No
- Default: `horizontal`

### tabs

A list of tabs where each tab is defined by an object with the following fields:

1. name: String. Defines the key for the tab
2. title: String. Defines the translated text for the tab
3. className: String. Defines the class to put on the tab.
4. onSelect: function taking tabName. This is called when the tab is selected.

- Type: Array
- Required: Yes

### activeClass

The class to add to the active tab

- Type: `String`
- Required: Yes

### children

A function which renders the tabviews given the selected tab. The function is passed a `tabName` as an argument.
The element to which the tooltip should anchor.

- Type: (`String`) => `Element`
- Required: Yes