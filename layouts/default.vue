<template>
	<div class="container mx-auto max-w-4xl">
		<header class="flex justify-between items-center mt-5">
			<div class="flex items-center">
				<div>
					<NuxtLink to="/" class="text-xl font-semibold p-2 hover:bg-gray-100">Main</NuxtLink>
				</div>
				
				<Menu />
			</div>

			<ClientOnly>
				<ColorModeSelector />
			</ClientOnly>
		</header>
		<slot />
	</div>
</template>

<script setup>
useHead({
	titleTemplate: '%s - Nezhurin Max'
})

</script>


