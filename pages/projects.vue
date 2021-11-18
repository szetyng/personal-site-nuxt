<template>
	<v-container>
		<v-row justify="center" >
			<v-col cols="12" md="10" lg="8">
			<OutlinedCard>
				<template v-slot:title>Projects</template>
				<template>
					<v-data-iterator
						:items="projects"
						hide-default-footer
						class="projects-iterator-container"
					>
						<template>
							<v-row justify="center">
								<v-col
									v-for="project in projects"
									:key="project.title"
									cols="12"
									sm="12" md="12" xl="6"
								>
									<v-card
										outlined flat
										min-height="300"
									>
										<!-- Top part of card: either an image of the project or the description of the project -->
										<!-- Image of the project  -->
										<v-card
											height="250px"
											flat
											class="scroll"
										>
											<v-img
												v-if="!project.expand"
												:src="require(`~/assets/images/portfolio/${project.imgSrc}`)"
												height="245px"
												class="project-img"
												contain
												@click="displayProjectInfo(project)"
											>
											</v-img>

										<!-- Description of the project -->
											<v-container v-else fluid>
												<!-- Close button at the top right corner -->
												<span class="card-right">
													<v-btn icon @click="closeProjectInfo(project)">
														<v-icon color="black">mdi-close</v-icon>
													</v-btn>
												</span>

												<!-- Description text in HTML because it includes links  -->
												<v-card-text class="project-text">
													<span v-html="project.description"></span>
												</v-card-text>

												<v-card-actions>
													<v-btn 
														v-for="(link, i) in project.links"
														:key="i"
														text outlined
														:color="link.color"
														:href="link.url"
													>
														{{ link.title }} 
														<v-icon right>{{ link.title | iconify }}</v-icon>
													</v-btn>
												</v-card-actions>

											</v-container>
										</v-card>

										<v-divider></v-divider>

										<!-- Bottom part of the card: always visible -->
										<!-- Title row: title + vertical dots icon button  -->
										<span class="card-right card-top">
											<v-btn icon @click="displayProjectInfo(project)">
												<v-icon color="black">
													mdi-dots-vertical
												</v-icon>
											</v-btn>
										</span>

										<v-card-title
											class="project-title text-h5 font-weight-light"
											style="word-break:break-word"
											@click="displayProjectInfo(project)"
										>
											{{ project.title }}
										</v-card-title>

										<!-- Github link to the project  -->
										<v-card-actions>
											<v-btn
												text
												:href="project.url"
												color="deep-orange accent-4"
											>
												Github
											</v-btn>
										</v-card-actions>
									</v-card>
								</v-col>
							</v-row>
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
	name: 'ProjectsPage',
	head() {
		return {
			title: 'Projects',
			meta: [
				{hid: 'description', name: 'description', content: 'Portfolifo of Sze Tyng Lee\'s projects'}
			]
		};
	},
	components: {
		OutlinedCard: () => import('@/components/OutlinedCard')
	},
	data() {
		return {
			projects: [
				{
					title: 'Wizarding World Metaverse Slayer',
					description: '\
					Simple turn-based NFT game built using Solidity. Each player\
					mints a Wizarding World character NFT that they can use to attack the Big Boss, Tom Riddle. The logic of the game is stored in a \
					smart contract that has been deployed on the Ethereum blockchain (on the Rinkeby test network), whereas the UI of the game is a\
					React.js web app written and hosted on <a href=\'https://replit.com/~\' target=\'_blank\'>replit</a>.  \
					',
					url: 'https://github.com/szetyng/NFT-magical-game',
					links: [
						{
							url: 'https://nft-game-starter-project.szetyngtyng.repl.co/',
							color: 'grey darken-2',
							title: 'Website'
						}
					],
					imgSrc: 'metaverse-slayer.png',
					expand: false
				},
				{
					title: 'Guardrails',
					description: '\
					Designed and built a multi-agent system simulator in F# to investigate the effects of having minimal \
					recognition of rights to self-organise (i.e. guardrails) on the sustainability of electronic institutions. Using \
					the method of sociologically-inspired computing, these institutions are designed according to the \
					<a href=\'https://en.wikipedia.org/wiki/Elinor_Ostrom#Design_principles_for_Common_Pool_Resource_(CPR)_institution\' target=\'_blank\'>principles</a> \
					proposed by political economist, Elinor Ostrom.\
					',
					url: 'https://github.com/szetyng/Guardrails',
					links: [
						{
							url: 'https://drive.google.com/open?id=1fzMeVbB9MzWxGHrpk6X85kNun_6NYvJ8OUVmduqiQtc',
							color: 'grey darken-2',
							title: 'Slides'
						}
					],
					imgSrc: 'institution.jpg',
					expand: false
				},
				{
					title: 'CaterPillar',
					description: '\
						  Developed a smart pill organiser to improve pill adherence and reduce medication errors among \
							the elderly. The CaterPillar system involves an electronic pillbox and Android applications for \
							tablets and smartwatches. It learns to provide adaptive reminders based on data regarding the \
							user\'s daily routines.\
					',
					url: 'https://github.com/szetyng/CaterPillar',
					links: [
						{
							url: 'https://youtu.be/Fv4SDEJEMSU',
							color: 'grey darken-2',
							title: 'Demo Video'
						}
					],
					imgSrc: 'caterpillar.png',
					expand: false
				},
				{
					title: 'neuron',
					description: '\
					  Collaborated with Microsoft to create an extension for Visual Studio Code, which has since been \
						<a href=\'https://blogs.msdn.microsoft.com/pythonengineering/2018/11/08/data-science-with-python-in-visual-studio-code/?fbclid=IwAR3M5REwXMSCxgCCiqKez_cMJr4WVYYy1DA3UjjjnhpNGDluQiSo4GnhBk0\' target=\'_blank\'>incorporated into their Python extension</a> \
						as part of their Data Science features. It combines the \
						rich experience of using the code editor with the interactive programming model of Jupyter notebook.\
					',
					url: 'https://github.com/neuron-team/vscode-ipe',
					links: [
						{
							url: 'https://youtu.be/amuV0z9eVg4',
							color: 'grey darken-2',
							title: 'Demo Video'
						}
					],
					imgSrc: 'neuron.png',
					expand: false
				},
				{
					title: 'Spam Detection',
					description: '\
						Applied the theory learned in Introduction to Machine Learning to classify emails as either spam or ham.\
					',
					url: 'https://github.com/szetyng/machine-learning-spam',
					imgSrc: 'laptop.png',
					expand: false
				},
				{
					title: 'ARM Emulator',
					description: '\
						Wrote and fully tested an ARM emulator in F#. The programme is able to parse and consecutively simulate a subset of the \
						ARM UAL instructions. Aimed to recreate <a href=\'https://salmanarif.bitbucket.io/visual/\' target=\'_blank\'>VisUAL</a>, \
						a visual ARM emulator used in Introduction to Computer Architecture in Imperial College London as an aide in teaching the \
						ARM assembly language.\
					',
					url: 'https://github.com/szetyng/HLP5',
					imgSrc: 'arm-emulator.png',
					expand: false
				},
				{
					title: 'AceCaddie',
					description: '\
						Used an accelerometer to build an IoT device that tracks golf scores automatically when it is \
						attached to the golf club in use. The accompanying mobile app allows friends to compete against each other.\
					',
					url: 'https://github.com/szetyng/embedded',
					links: [
						{
							url: 'https://dharshana1407.wixsite.com/acecaddie',
							color: 'grey darken-2',
							title: 'Website'
						}
					],
					imgSrc: 'acecaddie.png',
					expand: false
				},
				{
					title: 'SortBot',
					description: '\
						Implemented a classifier that uses machine vision to sort items into four different recycling categories \
						for a self-sorting recycling machine. Aims to encourage recyling on the Imperial College London campus by \
						awarding points to users of the machine through an accompanying mobile app.\
					',
					url: 'https://github.com/szetyng/sortbot',
					links: [
						{
							url: 'http://www.ee.ic.ac.uk/guo.liew15/yr2proj/default.htm',
							color: 'grey darken-2',
							title: 'Website'
						},
						{
							url: 'https://szetyng.github.io/assets/videos/sortbot.mp4',
							color: 'green darken-2',
							title: 'App Demo'
						}
					],
					imgSrc: 'sortbot.png',
					expand: false
				},
				{
					title: '2048',
					description: '\
						Recreated the popular 2048 game in C++.\
					',
					url: 'https://github.com/szetyng/2048',
					imgSrc: '2048.png',
					expand: false
				}
			]
		};
	},
	methods: {
		displayProjectInfo(project) {
			// console.log(project.title);

			project.expand = true;

			let projIdx = this.projects.findIndex(p => p.title === project.title);
			this.projects[projIdx] = project;
		},
		closeProjectInfo(project) {
			// console.log(project.title);

			project.expand = false;

			let projIdx = this.projects.findIndex(p => p.title === project.title);
			this.projects[projIdx] = project;
		}
	},
	filters: {
		iconify: title => {
			if (title === 'Website') {
				return 'mdi-open-in-app';
			} else if (title === 'App Demo' || title === 'Demo Video') {
				return 'mdi-video';
			} else if (title === 'Slides') {
				return 'mdi-play-box-outline';
			}
		}
	}
	
};
</script>


<style>
.projects-iterator-container {
	padding-left: 20px;
	padding-right: 20px;
}

.project-img {
	margin-left: auto;
	margin-right: auto;
	margin-top: auto;
	margin-bottom: auto;
	width: auto;
}

.project-img:hover {
	cursor: pointer;
}

.project-title:hover {
	cursor: pointer;
}

.project-expand:hover {
	cursor: pointer;
}

.card-right {
	float: right;
	margin-left: 15px;
}

.card-top {
	float: top;
	margin-top: 10px;
}

.scroll {
	overflow-y: auto;
}

.project-text a {
	text-decoration: none;
	border-bottom: black dotted 2px;
}
</style>