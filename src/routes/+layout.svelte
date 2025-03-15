<script lang="ts">
	import '@fontsource-variable/geist';
	import '../app.css';
	let { children } = $props();
</script>

<main class="p-10">
	{@render children()}
</main>
