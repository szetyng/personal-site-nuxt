<template>
  <v-container fluid>

    <v-row>

      <v-btn
        v-if="prev"
        left
        outlined large nuxt
        :to="{ name: 'blog-slug', params: { slug: prev.slug } }"
      >
        <v-icon>mdi-chevron-left</v-icon> Previous post
      </v-btn>

      <v-spacer></v-spacer>

      <v-btn
        v-if="next"
        right
        outlined large nuxt
        :to="{ name: 'blog-slug', params: { slug: next.slug } }"
      >
        Next post <v-icon>mdi-chevron-right</v-icon>
      </v-btn>

    </v-row>

  </v-container>

</template>


<script>
export default {
	props: {
		prev: {
			type: Object,
			default: () => null,
		},
		next: {
			type: Object,
			default: () => null,
		},
	},
};
</script>
