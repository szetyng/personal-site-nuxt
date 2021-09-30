<template>
	<v-container>
		<v-row justify="center">
				<v-col cols="12" md="10" lg="8">
					<OutlinedCard>
						<template v-slot:title>Blog</template>
						<template>
							<v-data-iterator
								:items="articles"
							>
								<template>
									<v-card 
										v-for="article of articles" :key="article.slug"
										outlined flat nuxt
										:to="{ name: 'blog-slug', params: { slug: article.slug } }"
										class="my-4 mx-4"
									>
										<!-- <img :src="article.img" /> -->
			
										<v-card-title class="article-title">{{ article.title }}</v-card-title>
										<v-card-subtitle>{{ article.description }}</v-card-subtitle>
										<v-card-actions>
											<v-chip
												v-for="tag in article.tags" :key="tag"
												outlined small color="teal darken-4"
												:ripple="false"
												class="mx-2 text-overline"
											>
												{{ tag }}
											</v-chip>
										</v-card-actions>
									</v-card>
								</template>
							</v-data-iterator>
						</template>
					</OutlinedCard>
			</v-col>
		</v-row>
	</v-container>
</template>


<script>
export default {
	name: 'BlogHomepage',
	head() {
		return {
			title: 'Blog',
			meta: [
				{hid: 'description', name: 'description', content: 'Sze Tyng Lee\'s blog.'}
			]
		};
	},
	components: {
		OutlinedCard: () => import('@/components/OutlinedCard')
	},
	async asyncData({ $content, }) {
		const articles = await $content('articles')
			.only(['title', 'description', 'img', 'slug', 'author', 'tags'])
			.sortBy('createdAt', 'desc')
			.fetch();

		return {
			articles,
		};
	},
};
</script>

<style scoped>
.article-title {
	/* Overwrite card title's word break properties */
	word-break: break-word;
}
</style>
