<template>
	<section class="not-prose font-mono">
		<div class="column text-gray-400 text-sm">
			<div>date</div>
			<div>title</div>
		</div>
	<ul>
		<li v-for="post in posts" :key="post._path">
			<NuxtLink :to="post._path" class="column group hover:bg-stone-200 dark:hover:bg-gray-800">
				<div :class="{'text-white group-hover:text-gray-100 dark:text-gray-900 dark:group-hove:text-gray-800': !post.displayYear, 'text-gray-400 dark:text-gray-500': post.displayYear }">{{ post.year }}</div>
				<div>{{ post.title }}</div>
			</NuxtLink>
		</li>
	</ul>
	</section>
	
</template>

<script setup>
const props = defineProps({
	limit: {
		type: Number,
		default: null
	}
})

const { data } = await useAsyncData(
	'blog-list',
	() => {
		const query = queryContent('/blog')
			.where({ _path: { $ne: '/blog' } })
			.only(['_path', 'title', 'publishedAt'])
			.sort({ publishedAt: -1 });


		if(props.limit) {
			query.limit(props.limit)
		}
		return query.find();
	}
);

const posts = computed(() => {
	const result = [];

	if(!data.value) {
		result [''];
	}

	let lastYear = null;

	for (const post of data.value) {
		const year = new Date(post.publishedAt).getFullYear();

		const displayYear = year !== lastYear;
		post.displayYear = displayYear;
		post.year = year;
		result.push(post);
		lastYear = year;
	}

	return result;
})
</script>

<style scoped>
.column {
	@apply flex items-center space-x-8 py-2 border-b border-gray-200
}
</style>