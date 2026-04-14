<script lang="ts">
	import type { Character } from '$lib/entities/character/types';

	export let characters: Character[] = [];
</script>

{#if characters.length === 0}
	<p class="empty">No hay resultados para ese filtro.</p>
{:else}
	<div class="grid">
		{#each characters as character}
			<article class="card">
				<div class="poster">
					<img src={character.image} alt={character.name} loading="lazy" />
					<span class:alive={character.status === 'Alive'} class:dead={character.status === 'Dead'}>
						{character.status}
					</span>
				</div>
				<div class="content">
					<h2>{character.name}</h2>
					<p>{character.species} / {character.gender}</p>
					<dl>
						<div>
							<dt>Origen</dt>
							<dd>{character.originName}</dd>
						</div>
						<div>
							<dt>Ubicacion</dt>
							<dd>{character.locationName}</dd>
						</div>
					</dl>
				</div>
			</article>
		{/each}
	</div>
{/if}

<style>
	.empty {
		margin: 2rem 0 0;
		color: #ffd447;
	}

	.grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
		gap: 1.1rem;
		align-items: start;
	}

	.card {
		position: relative;
		overflow: hidden;
		border-radius: 8px;
		border: 1px solid rgba(255, 255, 255, 0.12);
		background: #101010;
		box-shadow: 0 18px 42px rgba(0, 0, 0, 0.5);
		transition:
			transform 180ms ease,
			box-shadow 180ms ease,
			border-color 180ms ease;
	}

	.card:hover,
	.card:focus-within {
		transform: translateY(-6px) scale(1.03);
		border-color: #e50914;
		box-shadow:
			0 24px 64px rgba(0, 0, 0, 0.72),
			0 0 0 2px rgba(229, 9, 20, 0.95),
			0 0 34px rgba(0, 217, 255, 0.16);
		z-index: 2;
	}

	.poster {
		position: relative;
		aspect-ratio: 2 / 3;
		background: #050505;
	}

	img {
		display: block;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.poster::after {
		position: absolute;
		inset: auto 0 0;
		height: 54%;
		content: "";
		background: linear-gradient(180deg, transparent 0%, rgba(5, 5, 5, 0.9) 74%);
		pointer-events: none;
	}

	span {
		position: absolute;
		top: 0.7rem;
		left: 0.7rem;
		z-index: 1;
		padding: 0.28rem 0.55rem;
		border-radius: 999px;
		background: #ffd447;
		color: #050505;
		font-size: 0.72rem;
		font-weight: 900;
		text-transform: uppercase;
	}

	span.alive {
		background: #7cff6b;
	}

	span.dead {
		background: #e50914;
		color: #ffffff;
	}

	.content {
		min-height: 160px;
		padding: 0.95rem;
	}

	h2 {
		margin: 0 0 0.35rem;
		color: #ffffff;
		font-size: 1.04rem;
		line-height: 1.12;
	}

	p {
		margin: 0 0 0.9rem;
		color: #00d9ff;
		font-size: 0.88rem;
		font-weight: 700;
	}

	dl {
		margin: 0;
		display: grid;
		gap: 0.75rem;
	}

	dt {
		color: #b3b3b3;
		font-size: 0.74rem;
		letter-spacing: 0;
		text-transform: uppercase;
	}

	dd {
		margin: 0.2rem 0 0;
		color: #f5f5f5;
		font-size: 0.9rem;
		line-height: 1.25;
	}

	@media (max-width: 640px) {
		.grid {
			grid-template-columns: repeat(2, minmax(0, 1fr));
			gap: 0.75rem;
		}

		.content {
			min-height: 170px;
			padding: 0.8rem;
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.card {
			transition: none;
		}

		.card:hover,
		.card:focus-within {
			transform: none;
		}
	}
</style>
