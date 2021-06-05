<template>
	<v-app>
		<v-app-bar app color="primary" dark>
			<div class="d-flex align-center">
				<v-img
					alt="Vuetify Logo"
					class="shrink mr-2"
					contain
					src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
					transition="scale-transition"
					width="40"
				/>

				<v-img
					alt="Vuetify Name"
					class="shrink mt-1 hidden-sm-and-down"
					contain
					min-width="100"
					src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
					width="100"
				/>
			</div>

			<v-spacer></v-spacer>
			<div class="d-flex align-center justify-center">
				<v-btn
					href="https://github.com/vuetifyjs/vuetify/releases/latest"
					target="_blank"
					text
				>
					<span class="mr-2">Latest Release</span>
					<v-icon>mdi-open-in-new</v-icon>
				</v-btn>
				<v-switch
					v-model="themeToggle"
					:color="switchColor"
					:dark="!themeToggle"
					inset
					hide-details
					:label="`Set ${themeName} Mode`"
				></v-switch>
			</div>
		</v-app-bar>

		<v-main>
			<router-view />
		</v-main>
	</v-app>
</template>

<script>
export default {
	name: "App",

	data: () => ({
		themeToggle: false,
	}),
	computed: {
		themeName() {
			return this.themeToggle ? "Light" : "Dark";
		},
		switchColor() {
      // give color on dark
			return this.themeToggle ? "green" : "";
		},
	},
	watch: {
		themeToggle() {
			this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
		},
	},
};
</script>
