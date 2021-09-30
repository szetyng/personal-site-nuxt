<template>
  <v-container>
		<v-row dense>
			<v-col v-for="color in colors" :key="color" cols="3">
				<v-card :color="color">
					<v-card-title>{{ color }}</v-card-title>
				</v-card>

			</v-col>
		</v-row>
  </v-container>
</template>


<script>
export default {
	name: 'TestColorPage',
	data: () => {
		return {
			colors: [
				'primary',
				'secondary',
				'accent',
				'info',
				'warning',
				'error',
				'success',
				'lines'
			]
		};
	}
};
</script>