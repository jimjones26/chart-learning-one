<script lang="ts">
	import data from '$lib/data/data';
	import { max, scaleLinear } from 'd3';
	import AxisX from '$lib/components/AxisX.svelte';
	import AxisY from '$lib/components/AxisY.svelte';
	console.log(data);

	let width = 400;
	let height = 400;

	const margin = { top: 20, right: 40, left: 0, bottom: 20 };

	$: xScale = scaleLinear()
		.domain([0, 100])
		.range([0, width - margin.left - margin.right]);
	const yScale = scaleLinear()
		.domain([0, max(data, (d: any) => d.hours)])
		.range([height - margin.top - margin.bottom, 0]);
</script>

<div class="chart-container" bind:clientWidth={width}>
	<svg {height} {width}>
		<AxisX {height} {xScale} {margin} />
		<AxisY {width} {yScale} {margin} />
		<g class="circles" transform="translate({margin.left} {margin.top})">
			{#each data as student}
				<circle
					cx={xScale(student.grade)}
					cy={yScale(student.hours)}
					r="10"
					fill="purple"
					stroke="black"
				/>
			{/each}
		</g>
	</svg>
</div>
