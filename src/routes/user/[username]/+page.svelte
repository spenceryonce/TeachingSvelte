<script lang="ts">
	import { onMount } from 'svelte';
	let username: string;

	// Function to extract slug from the URL
	function getSlugFromUrl() {
		const path = window.location.pathname;
		const pathParts = path.split('/');

		// Assuming the slug is the last part of the URL after the last '/'
		return pathParts[pathParts.length - 1];
	}

	// Get the slug when the component is mounted
	onMount(() => {
		username = getSlugFromUrl();
	});
</script>

<main class="container">
    <div class="grid">
        <div style="border-radius:50%;height:50px;width:50px;background-color:white;"></div>
        <h1>{username}</h1>
    </div>
	
    <h6>One who likes to code. And piano. And languages. And stuff.</h6>
    <p>Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum Lorem ipsum </p>
</main>
