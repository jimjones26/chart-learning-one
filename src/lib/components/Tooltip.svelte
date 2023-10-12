<script lang="ts">
	export let hoveredData: any;
	export let xScale: any;
	export let yScale: any;
</script>

<div
	class="tooltip"
	style="position: absolute; top: {yScale(hoveredData.hours)}px; left: {xScale(
		hoveredData.grade
	)}px;"
>
	{hoveredData.name}
	{hoveredData.hours}
</div>

<style>
	.tooltip {
		padding: 6px;
		background: white;
		border: 1px solid #efefef;
		pointer-events: none;
		transition: top 300ms ease, left 300ms ease;
	}
</style>
