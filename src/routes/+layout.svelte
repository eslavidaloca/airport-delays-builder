<script lang="ts">
	// The ordering of these imports is critical to your app working properly
	import '@skeletonlabs/skeleton/themes/theme-gold-nouveau.css';
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	// Most of your app wide CSS should be put in this file
	import '../app.postcss';

	import {
		AppShell,
		AppBar,
		LightSwitch,
		AppRail,
		AppRailAnchor,
		AppRailTile,
		getDrawerStore,
		initializeStores,
		Toast
	} from '@skeletonlabs/skeleton';

	initializeStores();

	const drawerStore = getDrawerStore();

	import DrawerSkeleton from '../components/DrawerSkeleton.svelte';

	let currentTile: number = 0;

	$: positionClasses = $drawerStore.open ? 'translate-x-[50%]' : '';
</script>

<DrawerSkeleton />

<Toast />
				
<!-- App Shell -->
<AppShell class="transition-transform {positionClasses}">
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar gridColumns="grid-cols-3" slotDefault="place-self-center" slotTrail="place-content-end">
			<svelte:fragment slot="lead">(icon)</svelte:fragment>
			<span class="text-xl">DataPort</span>
			<svelte:fragment slot="trail">
				<LightSwitch bgLight='bg-primary-400 dark:bg-secondary-400'/>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<svelte:fragment slot="sidebarLeft">
		<AppRail>
			<div class="tiles">
				<AppRailTile bind:group={currentTile} name="Home" value={0} title="Home">
					<svelte:fragment slot="lead">
						<div class="flex justify-center">
							<i class="fa-solid fa-house"></i>
						</div>
					</svelte:fragment>
					<span>Home</span>
				</AppRailTile>
			</div>
			<div class="tiles">
				<AppRailTile bind:group={currentTile} name="Airports" value={1} title="Airports">
					<svelte:fragment slot="lead">
						<div class="flex justify-center">
							<i class="fas fa-cart-flatbed-suitcase" />
						</div>
					</svelte:fragment>
					<span>Airports</span>
				</AppRailTile>
			</div>
			<div class="tiles">
				<AppRailTile bind:group={currentTile} name="Flights" value={2} title="Flights">
					<svelte:fragment slot="lead">
						<div class="flex justify-center">
							<i class="fa-solid fa-plane-departure" />
						</div>
					</svelte:fragment>
					<span>Flights</span>
				</AppRailTile>
			</div>
			<!-- --- -->
			<svelte:fragment slot="trail">
				<AppRailAnchor href="/" target="_blank" title="Account">(icon)</AppRailAnchor>
			</svelte:fragment>
		</AppRail>
	</svelte:fragment>
	<!-- (sidebarRight) -->
	<svelte:fragment slot="pageHeader"><slot name="pageHeader"/></svelte:fragment>
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter"><slot name="pageFooter"/></svelte:fragment>
	<!-- (footer) -->
</AppShell>

<!-- App Bar -->
<!-- <AppBar>
	<svelte:fragment slot="lead">
		<strong class="text-xl">DAirTAport</strong>
	</svelte:fragment>
	<svelte:fragment slot="trail">
		<LightSwitch bgLight='bg-primary-400 dark:bg-secondary-400' />
		
	</svelte:fragment>
</AppBar> -->

<style>
	.tiles:hover div{
		animation: bounce 1s infinite; /* Aplicar la animación de brinco */
	}
</style>
