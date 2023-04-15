<script>
	import '../app.css';
</script>

<div class="flex">
	<nav class="w-[16rem] flex flex-col bg-[#f4f4f4] border-r border-gray-200">
		<div class="p-2">
			<span class="font-semibold">sidebar area</span>
		</div>
	</nav>
	<div class="flex-1 h-screen relative bg-yellow-100">
		<slot />
	</div>
</div>
