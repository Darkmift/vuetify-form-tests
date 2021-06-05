<template>
	<v-app>
		<v-container>
			<v-row class="text-center">
				<v-col cols="12"><main-form /> </v-col>
			</v-row>
		</v-container>
	</v-app>
</template>

<script>
import MainForm from "../components/MainForm";
export default {
	name: "Home",
	components: { MainForm },
};
</script>
