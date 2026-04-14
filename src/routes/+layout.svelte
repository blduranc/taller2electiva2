<svelte:head>
	<title>Prueba Lectiva</title>
	<meta
		name="description"
		content="Catalogo de personajes Rick and Morty con arquitectura feature-first/domain-first."
	/>
</svelte:head>

<div class="app-shell">
	<slot />
</div>

<style>
	:global(html) {
		color-scheme: dark;
	}

	:global(body) {
		margin: 0;
		font-family:
			Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
		background:
			linear-gradient(180deg, rgba(229, 9, 20, 0.22) 0%, transparent 22rem),
			radial-gradient(circle at 88% 8%, rgba(0, 217, 255, 0.22), transparent 20rem),
			#050505;
		color: #ffffff;
		min-height: 100vh;
	}

	.app-shell {
		min-height: 100vh;
	}
</style>
