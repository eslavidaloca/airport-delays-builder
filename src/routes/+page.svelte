<script>
	import { openDrawer } from "../components/DrawerSkeleton.svelte";
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h1 class="h1">Let's fly together today!</h1>
		<p>Start by choosing either option:</p>
		<div class="grid grid-cols-2 gap-2">
			<button class="btn variant-ghost-tertiary hover:bg-tertiary-700" on:click={() => openDrawer("left")}>Search flights</button>
			<button class="btn variant-ghost-tertiary hover:bg-tertiary-700" on:click={() => openDrawer("right")}>Search airports</button>
		</div>
	</div>
</div>
