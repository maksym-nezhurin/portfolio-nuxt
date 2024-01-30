<template>
	<NuxtLayout>
		<section>
			<h1>Ooop, {{ error.statusCode }}</h1>

			<h2>Page not fount {{ error.message }}</h2>
		</section>
	</NuxtLayout>
</template>

<script setup>
	defineProps({ error: Object })
</script>