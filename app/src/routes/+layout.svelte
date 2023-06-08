<script lang="ts">
	import '../app.css';
	import { page } from '$app/stores';
	import {
		DarkMode,
		Tooltip,
		Footer,
		FooterCopyright,
		FooterBrand,
		Navbar,
		NavBrand,
		NavUl,
		NavLi,
		NavHamburger
	} from 'flowbite-svelte';

	$: activeUrl = $page.url.pathname;
</script>

<Navbar
	color="default"
	fluid
	navClass="flex items-center justify-between w-full mx-auto py-1.5 px-4"
	let:hidden
	let:toggle
>
	<NavBrand>
		<img src="/favicon.png" class="mr-3 h-6 sm:h-9" alt="Logo" />
		<span class="self-center whitespace-nowrap text-xl font-black dark:text-white">
			App
		</span>
	</NavBrand>

	<div class="flex md:order-2">
		<DarkMode
			size="lg"
			initialTheme="dark"
			class="inline-block dark:hover:text-white hover:text-gray-900"
		/>
		<Tooltip class="dark:bg-gray-900" placement="bottom-end">Toggle dark mode</Tooltip>
		<NavHamburger on:click={toggle} />
	</div>

	<NavUl {hidden} class="order-1">
		<NavLi href="/" active={activeUrl.startsWith('/')}>
			<span class="text-base font-bold flex space-x-2">
				<span>Home</span>
			</span>
		</NavLi>
	</NavUl>
</Navbar>

<main class="mb-auto p-2">
	<slot />
</main>

<Footer footerType="logo" class="rounded-none">
	<div class="sm:flex sm:items-center sm:justify-between">
		<FooterBrand src="/favicon.png" alt="Logo" name="Logo" />
	</div>
	<hr class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8" />
	<FooterCopyright by="Svelte" />
</Footer>
