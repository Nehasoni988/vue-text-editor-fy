<template>
	<v-app id="app">
		<v-container fluid>
			<h1>Textarea</h1>
			<VueTextEditorFy
				:item="{
					id: 1,
					text: 'Dummy Text',
					bold: false,
					italic: false,
					color: '#000',
					background: '#FB8C01',
					fontSize: 'body-2',
					fontFamily: 'sans-serif',
				}"
			></VueTextEditorFy>

			<h1 class="mt-15">Textfield</h1>
			<VueTextEditorFy
				type="v-text-field"
				:item="{
					id: 2,
					text: 'Dummy Text',
					bold: false,
					italic: false,
					color: '#000',
					background: '#8BC34A',
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
