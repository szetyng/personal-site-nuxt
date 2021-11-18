<template>
	<v-container fill-height>
		<v-row justify="center" align="center">
			<v-col cols="12" md="10" lg="8" class="text-center">
				<OutlinedCard>
					<template>
						<v-container fluid>
						<v-row justify="center" align="center" no-gutters>
							<v-col cols="12" lg="4" class="szetyng-col">
								<v-row no-gutters justify="center" align="center">
									<v-col cols="12" class="text-center">
									<NuxtLink :to="'/about-me'">
									<v-img 
										contain width="15em" 
										class="rounded-circle profile-pic" 
										:src="require(`@/assets/images/bios/szetyng-sq.png`)"
									></v-img>
									</NuxtLink>
									</v-col>
								</v-row>
								<v-row no-gutters justify="center" align="center">
									<v-card-title class="text-center title-text">
										<NuxtLink :to="'/about-me'">Sze Tyng Lee</NuxtLink>
									</v-card-title>
								</v-row>
								<v-row no-gutters justify="center" align="center" class="subtitle-row">
									<v-card-subtitle class="job-title">
										<NuxtLink :to="'/about-me'">Software Developer</NuxtLink>
									</v-card-subtitle>
								</v-row>
							</v-col>

							<v-col cols="12" lg="8">
								<v-card-text class="black--text text-justify content-text introduction-text"> 
									<p>
									Hi there! I'm Sze Tyng, an MEng Electrical and Electronic Engineering graduate from Imperial
									College London. I am now a software developer currently based in Kuala Lumpur, Malaysia. 
									Feel free to wander around and let me know what you think. This site was built using 
									Nuxt.js + Vue.js by yours truly.
									</p>

									<p>
									It started off as a <NuxtLink :to="'/projects'">portfolio</NuxtLink> to showcase some of my personal
									projects, and I eventually added a <NuxtLink :to="'/blog'">blog</NuxtLink> section to share some of my 
									thoughts and musings with the world wide web!
									</p>

									<p>
									My CV is available upon request, just drop me a message at 
									<a href="mailto:lee.szetyng@gmail.com">lee.szetyng@gmail.com</a> 
									or contact me on any of the platforms linked below.
									</p>

							
								</v-card-text>


								
								<v-card-actions class="hidden-md-and-down">


									<v-btn
										v-for="contact in contacts"
										:key="contact.title"
										link
										:href="contact.link"
										:color="contact.color"
										text
										outlined
									>
										{{ contact.title }} <v-icon right>{{ contact.icon }}</v-icon>
									</v-btn>
				
								</v-card-actions>

								<v-card-actions class="hidden-lg-and-up">
									<v-spacer></v-spacer>
									<v-btn
										v-for="contact in contacts"
										:key="contact.title"
										link
										:href="contact.link"
										:color="contact.color"
										dark large
										icon text
									>
										<v-icon large>{{ contact.icon }}</v-icon>
									</v-btn>
									<v-spacer></v-spacer>

								</v-card-actions>
							</v-col>
						</v-row>
						</v-container>
					</template>
				</OutlinedCard>
	
			</v-col>
		</v-row>


		<v-row justify="center" align="center">
			<v-col cols="12" md="10" lg="8" class="text-center">
				<OutlinedCard>
					<template>
						<v-row justify="center" align="center">
							<v-card-title class="title-text">Skills</v-card-title>
						</v-row>
						<!-- <v-card-title class="title-text">Skills</v-card-title> -->
						<!-- <v-divider></v-divider> -->
						
						<v-row justify="center" align="center">
							<v-col class="icons-container" v-for="icon in icons" :key="icon.name" cols="4" md="2" lg="1">
								<v-tooltip 
									bottom
								>
									<template v-slot:activator="{ on, attrs }">
										<i 
											v-if="'link' in icon"
											v-bind="attrs" v-on="on"
											:class="`${icon.link} colored dev-icon`"
										>
										</i>

										<i
											v-else 
											v-bind="attrs" v-on="on"
											:class="`svg-icon icon-${icon.name}`"
										>
										</i>
									</template>

									<span>{{ icon.name }}</span>
								</v-tooltip>
							</v-col>
						</v-row>
					</template>
				</OutlinedCard>
			</v-col>
		</v-row>


			





	</v-container>
</template>


<script>
export default {
	name: 'Homepage',
	head() {
		return {
			title: 'Home',
			meta: [
				{hid: 'description', name: 'description', content: 'Homepage for Sze Tyng Lee\'s website'}
			],
			link: [
				{ rel: 'stylesheet', href: 'https://cdn.jsdelivr.net/gh/konpa/devicon@master/devicon.min.css' }
			]
		};
	},
	components: {
		OutlinedCard: () => import('@/components/OutlinedCard'),
	},
	data() {
		return {
			brief: '\
				Software developer. M.Eng Electrical and Electronic Engineering\
			',
			icons: [
				// {name: 'android', link: 'devicon-android-plain'},
				// {name: 'bootstrap', link: 'devicon-bootstrap-plain-wordmark'},
				{name: 'cplusplus', link: 'devicon-cplusplus-plain-wordmark'},
				{name: 'fastapi'},
				{name: 'fsharp'},
				{name: 'git', link: 'devicon-git-plain'},
				{name: 'googlecloudplatform'},
				{name: 'javascript', link: 'devicon-javascript-plain'},
				{name: 'nodejs', link: 'devicon-nodejs-plain-wordmark'},
				{name: 'nuxtjs'},
				{name: 'postgresql', link: 'devicon-postgresql-plain-wordmark'},
				{name: 'python'},
				{name: 'solidity'},
				{name: 'vuejs', link: 'devicon-vuejs-plain-wordmark'},
				
			],
			contacts: [
				{title: 'Github', link: 'https://github.com/szetyng', icon: 'mdi-github', color: 'grey darken-2'},
				{title: 'Twitter', link: 'https://twitter.com/szetyng', icon: 'mdi-twitter', color: 'blue lighten-1'},
				{title: 'LinkedIn', link: 'https://www.linkedin.com/in/leeszetyng/', icon: 'mdi-linkedin', color:'blue darken-2'},
				{title: 'Email', link: 'mailto:lee.szetyng@gmail.com', icon: 'mdi-email-outline', color: 'green darken-2'},
			]
		};
	}
};
</script>


<style scoped>
.svg-icon {
  height: 50px;
  width: 50px;
  display: inline-block;
}

.icon-fsharp {
  background: url("../assets/images/skills-icons/fsharp.svg");
}

.icon-python {
  background: no-repeat center/100%  url("../assets/images/skills-icons/python.svg");
}

.icon-googlecloudplatform {
	background: no-repeat center/100%  url("../assets/images/skills-icons/google-cloud-platform.svg");
}

.icon-nuxtjs {
	background: no-repeat center/100% url("../assets/images/skills-icons/nuxt.svg")
}

.icon-fastapi {
	background: no-repeat center/100% url("../assets/images/skills-icons/fastapi.png")
}

.icon-solidity {
	background: no-repeat center/100% url("../assets/images/skills-icons/solidity.png")
}

.icons-container {
	font-size: 50px;
	text-align: center;
	/* padding-top: 10px; */
	/* letter-spacing: 5px;	 */
}

.dev-icon {
	display: inline-block;
}

.dev-icon:hover, .svg-icon:hover {
	cursor: default;
}

.profile-pic {
	margin-left: auto;
	margin-right: auto;
}

.subtitle-row {
	margin-top: -30px;
}

.job-title {
	font-size: 15px;
	font-weight: 500;
	letter-spacing: 0.1em;
}

.szetyng-col a {
	text-decoration: none !important;
}

.introduction-text a {
	text-decoration: none;
	border-bottom: black dotted 2px;
}
</style>