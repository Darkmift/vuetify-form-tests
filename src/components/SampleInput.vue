<template>
	<v-text-field
		class="sample-input"
		:label="label"
		v-model="propModel"
		:required="required"
		:rules="rules"
	></v-text-field>
</template>

<style scoped></style>

<script>
export default {
	name: "sample-input",
	props: {
		label: { type: String },
		inputValue: { type: [Number, String] },
		rules: {
			type: Array,
			default: function () {
				return [];
			},
		},
		required: { type: Boolean, default: false },
	},
	computed: {
		propModel: {
			get() {
				return this.inputValue;
			},
			set(v) {
				// this.$emit("update:inputValue", v);
				this.$emit("setVal", v);
			},
		},
	},
};
</script>