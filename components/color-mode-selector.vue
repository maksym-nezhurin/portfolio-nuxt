<template>

	<div class="flex space-x-2 items-center">
		<div class="text-gray-500 text-cs" v-if="showNextModelLabel">Change to {{ nextMode }}</div>
		<button @click="toggleMode" @mouseenter="showNextModelLabel = true" @mouseleave="showNextModelLabel = false" class="hover:bg-gray-100 dark:hover:bg-gray-400 px-2 py-1">
			{{ nextModeIcon }}
		</button>
	</div>

</template>

<script setup>
	const showNextModelLabel = 	ref({value: false});
	const colorMode = useColorMode();
	const modes = [
		'system',
		'light',
		'dark'
	] // .length 3

	const nextModeIcons = {
		system: 'system',
		light: 'light',
		dark: 'dark',
	}

	const nextMode = computed(() => {
		const currentModeIndex = modes.indexOf(colorMode.preference);
		// const nextModeIndex = currentModeIndex + 1;
		let nextModeIndex = null;

		if(currentModeIndex + 1 === modes.length) {
			nextModeIndex = 0
		} else {
			nextModeIndex = currentModeIndex + 1;
		}

		return modes[nextModeIndex];
	})

	const nextModeIcon = computed(() => nextModeIcons[nextMode.value])

	const toggleMode = () => colorMode.preference = nextMode.value;
</script>

<style>
	body {
		background-color: #fff;
		color: rgba(0, 0, 0, 0.8);
	}

	.dark-mode body {
		background-color: #091a28;
		color: #ebf4f1;
	}

	.sepia-mode body {
		background-color: #f1e7d0;
		color: #433422;
	}
</style>

<style>
body {
	@apply bg-white dark:bg-gray-900 text-gray-700 dark:text-gray-300
}
</style>