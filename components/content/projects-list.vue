<template>
	<div class="not-prose">
		<section v-if="pending">Loading...</section>
		<section v-else-if="error">Something went wrong... Try again</section>
		<section v-else>Here we display the data
			<ul class="grid grid-cols-1 gap-4">
				<li v-for="repository in repos" :key="repository.id"
				class="border border-gray-200 rounded-sm hover:bg-gray-100 p-4">
					<a :href="repository.html_url" target="_blank" class="flex justify-between text-sm">
						<div class="font-semibold">
							{{ repository.name }}
							<br>
							{{ repository.description }}
						</div>
						<div>{{  repository.stargazers_count }} ☆</div>
					</a>
				</li>
			</ul>
		</section>
	</div>		
</template>

<script setup>
	const { error, pending, data } = await useFetch('https://api.github.com/users/maksym-nezhurin/repos');

	const repos = computed(
		() => data.value.filter((repo) => repo.description)
		.sort((a, b) => b.stargazers_count - a.stargazers_count)
	)
</script>