# vue-text-editor-fy

## Demo
![Demo](./src/assets/demo.gif)

## Requirements

```
"vue": "2.*",
"vuetify": "2.*"
```

## Installation

```
npm install --save vue-text-editor-fy
```
**or**
```
yarn add vue-text-editor-fy
```

**Import in any vue component**

```

import VueTextEditorFy from "vue-text-editor-fy"

components:{
  VueTextEditorFy
}
```

## Basic Usage

**Example-1**

```
<VueTextEditorFy
  type="v-text-field"
  :colors="['#000', '#fff']"
  :item="{
    id: 1,
    text: 'Dummy Text',
    bold: false,
    italic: false,
    color: '#000',
    background: '#607D8B',
    fontSize: 'body-2',
    fontFamily: 'sans-serif',

  }"
></VueTextEditorFy>
```
**Example-2**

```
<VueTextEditorFy
  :item="{
    id: 2,
    text: 'Dummy Text',
    bold: false,
    italic: false,
    color: '#000',
    background: '#607D8B'
  }"
></VueTextEditorFy>
```

## Properties

- `item`
  - **Type** - Object
  - **Required** - Yes
  - **Description** - This prop is going to have all values of edit propeties.
  - **Properties** -
     | Name | Type | Required | Description | Example Values |
     | ---- | ---- |--------- |------------ |--------------- |
     | id | Number/String | Yes | This is a unique value for each text component. | 1, 3816, 'abcd-234-sdf'|
     | text | String | Yes | The text to display | any string|
     | bold | Boolean | No | To bold the input text. | true/false |
     | italic | Boolean | No | To italic the text. | true/false |
     | color | String | No | To change the color of text. | any hex color value |
     | background | String | No | To change the background color of text field | any hex color value |
     | fontSize | String | No | To change the size of text | "subtitle-1","subtitle-2","body-1", "body-2","button","caption","overline" |
     | fontFamily | String | No | To change the background color of text field | "serif","sans-serif","monospace","cursive","fantasy","system-ui","ui-serif","ui-sans-serif","ui-monospace","ui-rounded","emoji","math","fangsong" |

- `type`
  - **Type** - String
  - **Required** - No
  - **Description** - To decide the type on text box, either textarea of input.
  - **Default** - "v-textarea"
  - **Support values** - "v-text-field", "v-textarea"

- `colors`
  - **Type** - Array
  - **Required** - No
  - **Description** - Choices for background and font colors.
  - **Default** - ["#F5F5F5", "#FFAC77", "#FFEB3B", "#CDDC39", "#41BBB4", "#FFC107", "#8BC34A", "#F587C7", "#FB8C01", "#4CAF50","#2196F3", "#607D8B","#E53935", "#1A76D2", "#E91E63", "#795548", "#9C27B0", "#000000"]
  - **Support values** - Array of any number of hex color values.

## License
This project is licensed under the MIT License - see the [LICENSE.md](License) file for details.



