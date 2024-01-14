
# svelte-textarea-autosize

textarea autosize input component for the web built with svelte.


## Installation

Install my-project with npm

```bash
 npm i svelte-textarea-autosize
```

    
## Usage/Examples

```html

 <script type="ts">
    import SvelteAutoResizeTextarea from 'svelte-textarea-autosize';
    let inputValue: string = ''
 </script>
  <SvelteAutoResizeTextarea
    textareaStyle="width: 300px;"
    className="my-custom-class"
    bind:textareaValue={inputValue}
    minRows={2}
    maxRows={5}
    onHeightChange={(height) => console.log(`Height changed to ${height}px`)}
    onPressEnter={() => console.log("Enter key pressed")}
    placeholder="Type something..."
  />
```

## Props

| **Name**         | **Type**                                       | **Required** | **Default** |
|------------------|------------------------------------------------|:------------:|:-----------:|
| textareaValue    | String                                         |     true     |      -      |
| textareaStyle    | String                                         |     false    |      -      |
| className        | String                                         |     false    |      -      |
| minRows          | Number                                         |     false    |      2      |
| maxRows          | Number                                         |     false    |      3      |
| onHeightChange   | Function ((height: string \| number) => void)  |     false    |      -      |
| onPressEnter     | Function (() => void)                          |     false    |      -      |
| placeholder      | String                                         |     false    |      -      |
| fontSize         | Number (default: 16)                           |     false    |      16     |

