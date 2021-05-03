<template>
	<v-app id="app">
		<v-container fluid>
			<VueTextEditorFy
				:item="{
					id: 1,
					text: 'Dummy Text',
					bold: false,
					italic: false,
					color: '#000',
					background: '#607D8B',
					fontSize: 'body-2',
					fontFamily: 'sans-serif',
				}"
			></VueTextEditorFy>
		</v-container>
	</v-app>
</template>

<script>
import VueTextEditorFy from "./components/VueTextEditorFy";

export default {
	name: "App",
	components: {
		VueTextEditorFy,
	},
};
</script>

<style></style>
