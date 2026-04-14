<script lang="ts">
	export let query: string = '';
	export let onQueryChange: (value: string) => void;
</script>

<label class="search">
	<span>Buscar personaje</span>
	<input
		type="search"
		placeholder="Rick, Morty, Summer..."
		value={query}
		on:input={(event) => onQueryChange((event.currentTarget as HTMLInputElement).value)}
	/>
</label>

<style>
	.search {
		display: grid;
		gap: 0.55rem;
	}

	.search span {
		color: #f5f5f5;
		font-size: 0.92rem;
		font-weight: 700;
	}

	input {
		width: 100%;
		box-sizing: border-box;
		border: 1px solid rgba(255, 255, 255, 0.24);
		background: #101010;
		color: #ffffff;
		padding: 1rem 1.05rem;
		border-radius: 8px;
		outline: none;
		box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.04);
	}

	input::placeholder {
		color: #b3b3b3;
	}

	input:focus {
		border-color: #00d9ff;
		box-shadow:
			0 0 0 3px rgba(0, 217, 255, 0.18),
			0 0 36px rgba(0, 217, 255, 0.18);
	}
</style>
