<template>
	<v-form ref="form" v-model="valid" class="main-form" lazy-validation>
		<v-text-field
			v-model="name"
			:counter="10"
			:rules="nameRules"
			label="Name"
			required
		></v-text-field>

		<sample-input
			label="Sample"
			:inputValue="inputText"
			:rules="nameRules"
			@setVal="inputText = $event"
		/>

		<v-btn
			:disabled="!valid"
			:style="{
				'background-color': !valid ? `var(--v-success)` : '',
			}"
			color="success"
			class="mr-4"
			@click="validate"
		>
			Validate
		</v-btn>

		<v-btn color="error" class="mr-4" @click="reset"> Reset Form </v-btn>

		<v-btn color="warning" @click="resetValidation">
			Reset Validation
		</v-btn>
	</v-form>
</template>

<style scoped lang="scss">
// @import "~vuetify/src/styles/styles.sass";
// .v-btn {
// 	background-color: #4caf50;
// 	color: white;
// 	&.v-btn--disabled {
// 		&.v-btn--has-bg {
// 			background-color: inherit !important;
// 			color: inherit !important;
// 			opacity: 0.5;
// 		}
// 	}
// }
</style>

<script>
import SampleInput from "./SampleInput.vue";
export default {
	components: { SampleInput },
	name: "Main-Form",
	data() {
		return {
			valid: true,
			name: "",
			inputText: "inputText string",
			nameRules: [
				(v) => !!v || "Name is required",
				(v) =>
					(v && v.length <= 10) ||
					"Name must be less than 10 characters",
			],
			email: "",
			emailRules: [
				(v) => !!v || "E-mail is required",
				(v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
			],
			select: null,
			items: ["Item 1", "Item 2", "Item 3", "Item 4"],
			checkbox: false,
		};
	},

	methods: {
		validate() {
			console.log(this.inputText, this.valid, this.$refs.form.validate());
		},
		reset() {
			this.$refs.form.reset();
		},
		resetValidation() {
			this.$refs.form.resetValidation();
		},
	},
};
</script>