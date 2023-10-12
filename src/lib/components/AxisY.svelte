<script lang="ts">
	export let width: number;
	export let yScale: any;
	export let margin: any;

	let yTicks = [0, 20, 40, 60];
</script>

<g transform="translate({margin.left} {margin.top})">
	{#each yTicks as tick}
		<text x={0} y={yScale(tick)} dy="-6">{tick}</text>
		<line x1="0" y1={yScale(tick)} x2={width} y2={yScale(tick)} stroke="#cecece" />
	{/each}
</g>
