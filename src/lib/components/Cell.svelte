<script lang="ts">
	import type { Piece } from '$lib/types';
	export let piece: Piece;
	export let alternate: boolean;
</script>

<button on:click aria-hidden="true" class="cell" class:alternate>
	<span
		class:possibleMove={piece.possible}
		class:piece={piece?.player != null}
		class:red={piece?.player == 1}
		class:blue={piece?.player == 2}
		class:selected={piece.selected}
	>
	</span>
</button>

<!-- svelte-ignore css_unused_selector -->
<style lang="scss">
	.cell {
		display: flex;
		justify-content: center;
		align-items: center;
		aspect-ratio: 1;
		background-color: var(--cell-default);

		border: none;
		outline: none;

		user-select: none;
		cursor: pointer;

		&.alternate {
			background-color: var(--alternate-cell-default);
		}
	}

	.piece {
		width: calc(var(--cell-size) * 0.65);
		position: absolute;
		aspect-ratio: 1;
		background-color: var(--red-player-fill);
		border-radius: 50%;
		border: var(--stroke-width) solid gray;
	}

	.red {
		background-color: var(--red-player-fill);
		border: var(--stroke-width) solid var(--red-player-border);
	}

	.blue {
		background-color: var(--blue-player-fill);
		border: var(--stroke-width) solid var(--blue-player-border);
	}

	.possibleMove {
		width: calc(var(--cell-size) * 0.3);
		position: absolute;
		aspect-ratio: 1;
		background-color: rgba(0, 0, 0, 0.15);
		border-radius: 50%;
	}

	.selected {
		opacity: 0.6;
	}
</style>
