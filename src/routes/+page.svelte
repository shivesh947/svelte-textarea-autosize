<script type="ts" lang="ts">
  import SvelteAutoResizeTextarea from "../lib/svelte-textarea-autosize.svelte";
  let inputValue: string = ''
</script>

<h1>Welcome to your library project</h1>
<p>{inputValue}</p>
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