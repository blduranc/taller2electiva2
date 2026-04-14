<script lang="ts">
	import { CharacterList } from '$lib/features/character-list';
	import { CharacterSearch } from '$lib/features/character-search';
	import type { CharacterBrowserData } from '../model';

	export let data: CharacterBrowserData;
	export let onQueryChange: (value: string) => void;
</script>

<section class="hero">
	<div class="eyebrow">Rick and Morty Streaming</div>
	<h1>Personajes en modo multiverso.</h1>
	<p>Explora favoritos, rarezas y variantes con una vitrina oscura de alto contraste.</p>
</section>

<section class="catalog">
	<CharacterSearch query={data.query} onQueryChange={onQueryChange} />

	<div class="meta">
		<p><strong>{data.total}</strong> personajes disponibles</p>
		{#if data.error}
			<p class="error">{data.error}</p>
		{/if}
	</div>

	<CharacterList characters={data.characters} />
</section>

<style>
	section.hero {
		max-width: 1180px;
		margin: 0 auto;
		padding: 4.5rem 1.25rem 2rem;
	}

	.eyebrow {
		display: inline-flex;
		padding: 0.45rem 0.8rem;
		border-radius: 999px;
		background: #e50914;
		color: #ffffff;
		font-size: 0.8rem;
		font-weight: 800;
		letter-spacing: 0;
		text-transform: uppercase;
		box-shadow: 0 0 28px rgba(229, 9, 20, 0.42);
	}

	h1 {
		max-width: 13ch;
		margin: 1rem 0 0.8rem;
		font-size: clamp(2.5rem, 4.6rem, 4.6rem);
		line-height: 0.95;
		text-wrap: balance;
	}

	p {
		max-width: 60ch;
		margin: 0;
		color: #d8d8d8;
		font-size: 1.08rem;
	}

	.catalog {
		max-width: 1180px;
		margin: 0 auto;
		padding: 0 1.25rem 4rem;
		display: grid;
		gap: 1.25rem;
	}

	.meta {
		display: flex;
		justify-content: space-between;
		gap: 1rem;
		align-items: center;
	}

	.meta p {
		margin: 0;
		color: #b3b3b3;
		font-size: 0.95rem;
	}

	.meta strong {
		color: #7cff6b;
	}

	.error {
		color: #ffd447;
	}

	@media (max-width: 640px) {
		section.hero {
			padding-top: 3rem;
		}

		h1 {
			font-size: 2.6rem;
		}

		.meta {
			align-items: flex-start;
			flex-direction: column;
		}
	}
</style>
