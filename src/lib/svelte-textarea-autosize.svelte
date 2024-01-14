<script lang="ts" type="ts">
	import { onMount } from "svelte";
  
	export let textareaValue = "";
	export let textareaStyle: string = "";
	export let className: string = "";
	export let minRows: number | undefined = 2;
	export let maxRows: number | undefined = 3;
	export let onHeightChange: ((height: string | number) => void) | undefined = undefined;
	export let onPressEnter: (() => void) | undefined = undefined;
	export let placeholder:string | undefined = "";
	export let fontSize:number = 16;

	let textareaRef: HTMLTextAreaElement | null = null;
  
	onMount(() => {
	  if (textareaRef) {
		textareaRef.style.fontSize = `${fontSize}px`;
		adjustTextareaHeight();
	  }
	});
  
	function handleInput(event: Event & { currentTarget: EventTarget & HTMLTextAreaElement; }) {
	  textareaValue = (event.target as HTMLTextAreaElement).value;
	  adjustTextareaHeight();
	}
  
	function handleKeyPress(event: KeyboardEvent) {
	  if (event.key === "Enter" && onPressEnter) {
		onPressEnter();
	  }
	}
  
	function adjustTextareaHeight() {
	  if (textareaRef) {
		textareaRef.style.height = "auto";
		textareaRef.style.height = `${textareaRef.scrollHeight}px`;
  
		if (onHeightChange) {
		  onHeightChange(textareaRef.scrollHeight);
		}
  
		if (maxRows) {
		  const maxHeight = (maxRows+2) * fontSize;
		  if (textareaRef.scrollHeight > maxHeight) {
			textareaRef.style.overflowY = "scroll";
			textareaRef.style.height = `${maxHeight}px`;
		  } else {
			textareaRef.style.overflowY = "hidden";
		  }
		}
	  }
	}
  </script>
  
  <style>
	textarea {
	  resize: none;
	  box-sizing: border-box;
	}
  </style>
  
  <textarea
	bind:value={textareaValue}
	bind:this={textareaRef}
	style={textareaStyle}
	class={className}
	rows={minRows}
	placeholder={placeholder}
	on:input={handleInput}
	on:keypress={handleKeyPress}
  ></textarea>
  