<script lang="ts">
	import { invoke } from '@tauri-apps/api/tauri';
	import { Button } from 'flowbite-svelte';

	let name: string = '';
	let greetMsg: string = '';

	async function greet() {
		greetMsg = await invoke<string>('greet', { name });
	}
</script>

<div>
	<input id="greet-input" placeholder="Enter a name..." bind:value={name} />
	<Button on:click={greet}>Greet</Button>
	<p>{greetMsg}</p>
</div>
