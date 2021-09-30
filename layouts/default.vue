<template>
  <v-app>
		<!-- Navbar in desktop - a horizontal toolbar -->
    <v-app-bar app flat hide-on-scroll class="normal-navbar hidden-sm-and-down">
      <v-container>
        <!-- Justify center to make sure that the 8 cols are in the middle -->
        <v-row justify="center">
          <v-col cols="12" md="10" lg="8">
						<a href="/" class="title-text">{{ title }}</a>
            <v-spacer></v-spacer>
            <div class="nav">
              <a 
                v-for="(item, i) in links"
                :key="i"
                :href="item.link"
              >
                {{ item.title }}
              </a>
            </div>
          </v-col>
        </v-row>      
      </v-container>
    </v-app-bar>

		<!-- Navbar in mobile - a horizontal toolbar with title and hamburger setting -->
    <v-app-bar app flat class="mobile-navbar hidden-md-and-up">
      <v-toolbar-title>
        <a href="/" class="title-text">{{ title }}</a>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    </v-app-bar>

		<!-- Nav drawer for mobile -->
		<v-navigation-drawer app right temporary class="nav-drawer" v-model="drawer">
			<v-list dense nav>
				<v-list-item v-for="(item, i) in links" :key="i" nuxt :to="item.link" class="link">
          <v-list-item-content>
            <v-list-item-title class="text-uppercase title-text">
              {{ item.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
			</v-list>
		</v-navigation-drawer>

    <v-main>
      <v-container class="main-container">
        <nuxt />
      </v-container>
    </v-main>

    <v-footer absolute app padless>
      <v-row justify="center" no-gutters>
        <v-col cols="12" class="text-center">
          <v-card color="secondary" flat tile class="text-center">
            <v-card-text>
              <v-btn
                v-for="social in socials"
                :key="social.icon"
                class="mx-4"
                icon link
								:href="social.link"
              >
                <v-icon>{{ social.icon }}</v-icon>

              </v-btn>
            </v-card-text>
						
              <!-- {{ screenSize }} -->
						
            <v-card-text class="footer-text">
              <span>&copy; {{ new Date().getFullYear() }} {{ footer }}</span>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
      
    </v-footer>
  </v-app>
</template>

<script>
export default {
	name: 'DefaultLayout',
	data () {
		return {
			title: 'Sze Tyng Lee',
			drawer: false,
			footer: 'Copyright Sze Tyng Lee | All rights reserved',
			links: [
				{title: 'about me', link: '/about-me'},
				{title: 'projects', link: '/projects'},
				// {title: 'experience', link: '/experience'},
				{title: 'blog', link: '/blog'},
				// {title: 'contact me', link: '/contact'}
			],
			socials: [
				{title: 'Github', link: 'https://github.com/szetyng', icon: 'mdi-github', color: 'grey darken-2'},
				{title: 'Twitter', link: 'https://twitter.com/szetyng', icon: 'mdi-twitter', color: 'blue lighten-1'},
				{title: 'LinkedIn', link: 'https://www.linkedin.com/in/leeszetyng/', icon: 'mdi-linkedin', color:'blue darken-2'},
				{title: 'Email', link: 'mailto:lee.szetyng@gmail.com', icon: 'mdi-email-outline', color: 'green darken-2'},
			]
		};
	},

	computed: {
		screenSize() {
			if (this.$vuetify.breakpoint.xs) return 'xs';
			else if (this.$vuetify.breakpoint.sm) return 'sm';
			else if (this.$vuetify.breakpoint.md) return 'md';
			else if (this.$vuetify.breakpoint.lg) return 'lg';
			else if (this.$vuetify.breakpoint.xl) return 'xl';
			else return 'error';
		}
	}
};
</script>


<style>
/* Unscoped CSS, to be made available to every component when THIS
component is loaded */
.title-text {
  font-size: 22px !important;
  font-weight: 600;
	line-height: 2rem;
	letter-spacing: 0.1em;
	font-family: "Roboto", sans-serif;
	text-transform: uppercase;
  /* Overwrite card title's word break properties */
	word-break: break-word;
}

.content-text {
	font-size: 16px !important;
}
</style>


<style scoped>
/* Set default background color of app, since this is default layout */
.v-application {
  background-color: #F4F4F4;
}


/* To make links in the nav drawer have more space */
.nav-drawer {
	padding: 2.5em 1.5em 0;
}

.title-text {
	float: left;
	letter-spacing: 0.1em;
	font-size: 18px !important;
  font-family: "Helvetica", "sans-serif";
}

.footer-text {
	margin-top: -25px;
}

.main-container {
	margin-top: -15px;
}

/* All the links in the mobile horizontal navbar */
.mobile-navbar a {
  margin-left: 10px;
  text-decoration: none;
  cursor: pointer;
}

/* All the links in the mobile horizontal navbar, on hover */
.mobile-navbar a:hover {
  color: cadetblue;
}

/* All the list items in the nav drawer */
.nav-drawer .link {
  margin: 1.5em 0 0 0;
  padding: 0.5em 0 0 0.5em;
}

/* The links container in the normal navbar */
.normal-navbar .nav {
  float: right;
  /* font-size: 20px; */
  font-weight: 600;
	margin-right: 10px;
	font-family: "Helvetica", "sans-serif";
}

/* Links in the nav (pages) part of navbar */
.normal-navbar .nav a {
	margin-left: 20px;
  color: #333;
  text-decoration: none;
  cursor: pointer;
	text-align: right;
	letter-spacing: 1px;
	text-transform: uppercase;
}


/* Links in the navbar */
.normal-navbar a {
  margin-left: 10px;
  text-decoration: none;
  cursor: pointer;
	text-align: right;
	font-size: 18px;
}

/* All the links in the normal horizontal navbar, on hover */
.normal-navbar a:hover {
  color: cadetblue;
}


</style>
