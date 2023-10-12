<script lang="ts">
	import data from '$lib/data/data';
	import { max, scaleLinear } from 'd3';
	import AxisX from '$lib/components/AxisX.svelte';
	console.log(data);

	let width = 400;
	let height = 400;

	const xScale = scaleLinear().domain([0, 100]).range([0, width]);
	const yScale = scaleLinear()
		.domain([0, max(data, (d: any) => d.hours)])
		.range([height, 0]);
</script>

<svg {height} {width}>
	<AxisX {height} {xScale} />
	{#each data as student}
		<circle
			cx={xScale(student.grade)}
			cy={yScale(student.hours)}
			r="10"
			fill="purple"
			stroke="black"
		/>
	{/each}
</svg>
