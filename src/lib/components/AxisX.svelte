<script lang="ts">
	export let height: number;
	export let xScale: any;
	export let margin: any;

	let xTicks = [0, 25, 50, 75, 100];
</script>

<g>
	{#each xTicks as tick}
		<text x={xScale(tick)} y={height - margin.bottom} dominant-baseline="hanging" dy="6"
			>{tick}%</text
		>
	{/each}
</g>
