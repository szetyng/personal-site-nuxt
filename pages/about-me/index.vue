<template>
	<v-container>
		<v-row justify="center">
			<v-col cols="12" md="10" lg="8">
				<OutlinedCard>
						<template v-slot:title>{{ article.title }}</template>
						<template v-slot:subtitle>Post last updated at: {{ article.updatedAt | formatDate }}</template>
						
						<template v-slot:defaultContent>
							<nuxt-content :document="article" />
						</template>
				</OutlinedCard>

			</v-col>
		</v-row>
	</v-container>
</template>


<script>
export default {
	head() {
		return {
			title: 'About',
			meta: [
				{hid: 'description', name: 'description', content: 'About Sze Tyng Lee'}
			]
		};
	},
	components: {
		OutlinedCard: () => import('@/components/OutlinedCard')
	},
	async asyncData ({ $content, }) {
		const article = await $content('about-me').fetch();

		return { article };
	},

	filters: {
		formatDate: dt => {
			const options = { year: 'numeric', month: 'long', day: 'numeric'};

			return new Date(dt).toLocaleDateString('en', options);
		}
	}
};
</script>


<style>
.nuxt-content img {
	display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
	border-radius: 50%;
}

.nuxt-content a {
	text-decoration: none;
	border-bottom: black dotted 2px;
}
</style>