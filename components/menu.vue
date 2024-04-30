<template>
	<nav>
		<ul class="flex flex-col md:flex-row md:space-x-4">
			<li>
				<NuxtLink href="/" class="link" >
					Main
				</NuxtLink>
			</li>
			<li>
				<NuxtLink href="/about" class=" link">
					About
				</NuxtLink>
			</li>

			<li>
				<NuxtLink href="/projects" class=" link">
					Projects
				</NuxtLink>
			</li>

			<li>
				<NuxtLink href="/blog" class=" link">
					Blog
				</NuxtLink>
			</li>
		</ul>
	</nav>
</template>

<style scoped>
	.link {
		@apply p-1 hover:bg-gray-200;
		margin: 2px;
	}
</style>