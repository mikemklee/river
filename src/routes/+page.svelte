<script lang="ts">
	import { onMount } from 'svelte';

	import Svelvet from 'svelvet';
	import type { UserNodeType, UserEdgeType } from 'svelvet';
	const initialNodes: UserNodeType[] = [
		{
			id: 1,
			position: { x: 0, y: 0 },
			data: { label: 'Input Node' },
			width: 175,
			height: 40,
			bgColor: 'white'
		},
		{
			id: 2,
			position: { x: 10, y: 10 },
			data: { label: 'Option #1' },
			width: 175,
			height: 40,
			bgColor: '#B8FFC6',
			borderColor: 'transparent'
		},
		{
			id: 3,
			position: { x: 20, y: 20 },
			data: { label: 'Option #2' },
			width: 175,
			height: 40,
			bgColor: '#FFB8B8',
			borderColor: 'transparent'
		}
	];
	const initialEdges: UserEdgeType[] = [
		{ id: 'e1-2', source: 1, target: 2, label: ' YES ', animate: true },
		{ id: 'e2-3', source: 1, target: 3, label: ' NO ', animate: true }
	];

	let container;
	let containerWidth = 0;
	let containerHeight = 0;
	let isInitialized = false;

	function updateContainerSize() {
		containerWidth = container.clientWidth;
		containerHeight = container.clientHeight;
		isInitialized = true;
		console.log(containerWidth, containerHeight);
	}

	onMount(() => {
		window.addEventListener('resize', updateContainerSize);

		updateContainerSize();
		return () => {
			window.removeEventListener('resize', updateContainerSize);
		};
	});
</script>

<div class="w-full h-full" bind:this={container}>
	{#if isInitialized}
		<Svelvet
			width={containerWidth}
			height={containerHeight}
			nodes={initialNodes}
			edges={initialEdges}
			background
		/>
	{/if}
</div>
