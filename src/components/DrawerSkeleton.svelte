<script context="module" lang="ts">
	import { Drawer, getDrawerStore  } from '@skeletonlabs/skeleton';
	import type { DrawerSettings, DrawerStore } from '@skeletonlabs/skeleton';

	const drawerStore = getDrawerStore();

	const DrawerLeftSettings: DrawerSettings = {
		id: 'leftDrawer',
		bgBackdrop:
			'bg-gradient-to-tr from-surface-900/50 via-tertiary-500/50 to-secondary-500/50',
		width: 'w-8/12 md:w-10/12',
		padding: 'p-4',
		rounded: 'rounded-xl'
	};
	const DrawerRightSettings: DrawerSettings = {
		id: 'RightDrawer',
		bgBackdrop:
			'bg-gradient-to-tr from-primary-500/50 dark:from-secondary-500/50 via-tertiary-500/50 to-secondary-500/50 dark:to-primary-500/50',
		width: 'w-8/12 md:w-10/12',
		padding: 'p-4',
		rounded: 'rounded-xl'
	};

	export function openDrawer(position: "right" | "left") {
    if (position === 'left') 
      drawerStore.open(DrawerLeftSettings);
     else if (position === 'right') 
      drawerStore.open(DrawerRightSettings);

  }
</script>

{#if $drawerStore.id === 'leftDrawer'}
	<Drawer position="left">
		<div class="bg-primary-400 dark:bg-secondary-400">
			Hola
		</div>
	</Drawer>
	{:else}
	<Drawer position="right">
		adios
	</Drawer>
	{/if}
