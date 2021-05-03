<template>
	<v-btn-toggle>
		<!-- Background color -->
		<v-menu
			:close-on-content-click="false"
			offset-x
			v-if="isPropertyExist('background')"
		>
			<template v-slot:activator="{ on, attrs }">
				<v-btn v-bind="attrs" v-on="on" color="white">
					<v-icon :color="item.background">mdi-checkbox-blank</v-icon>
				</v-btn>
			</template>
			<v-card width="100" align="center">
				<v-card-text class="px-1">
					<v-icon
						v-for="(hex_value, index) in colors_array"
						:key="index"
						:color="hex_value"
						:class="{
							'highlight-class-wr': item.background == hex_value,
							'cursor-wr': true,
						}"
						@click="
							$emit('update-style', {
								attribute: 'background',
								value: hex_value,
							})
						"
						>mdi-checkbox-blank</v-icon
					>
				</v-card-text>
			</v-card>
		</v-menu>

		<!-- Font family -->
		<v-menu
			top
			:close-on-content-click="false"
			offset-x
			v-if="isPropertyExist('fontFamily')"
		>
			<template v-slot:activator="{ on, attrs }">
				<v-btn color="white" class="text-capitalize" v-bind="attrs" v-on="on">
					{{ item.fontFamily }}
				</v-btn>
			</template>
			<v-card width="100" align="center">
				<v-card-text class="px-1">
					<div
						v-for="(family, index) in font_families"
						:key="index"
						:class="{
							'cursor-wr black--text pa-1': true,
							'font-weight-bold red--text': item.fontFamily == family,
						}"
						:style="{ fontFamily: family }"
						@click="
							$emit('update-style', {
								attribute: 'fontFamily',
								value: family,
							})
						"
					>
						{{ family }}
					</div>
				</v-card-text>
			</v-card>
		</v-menu>

		<!-- Font size -->
		<v-menu
			top
			:close-on-content-click="false"
			offset-y
			v-if="isPropertyExist('fontSize')"
		>
			<template v-slot:activator="{ on, attrs }">
				<v-btn v-bind="attrs" v-on="on">
					<v-icon>mdi-format-size</v-icon>
				</v-btn>
			</template>
			<v-card width="70" align="center">
				<v-card-text class="px-1">
					<div
						v-for="(font, index) in font_sizes"
						:key="index"
						:class="[
							font,
							{
								'cursor-wr black--text pa-1': true,
								'font-weight-bold red--text': item.fontSize == font,
							},
						]"
						@click="
							$emit('update-style', {
								attribute: 'fontSize',
								value: font,
							})
						"
					>
						Text
					</div>
				</v-card-text>
			</v-card>
		</v-menu>

		<!-- Bold -->
		<v-btn
			v-if="isPropertyExist('bold')"
			:color="item.bold ? 'grey lighten-3' : 'white'"
			@click="
				$emit('update-style', {
					attribute: 'bold',
					value: !item.bold,
				})
			"
		>
			<v-icon>mdi-format-bold</v-icon>
		</v-btn>

		<!-- Italic -->
		<v-btn
			v-if="isPropertyExist('italic')"
			:color="item.italic ? 'grey lighten-3' : 'white'"
			@click="
				$emit('update-style', {
					attribute: 'italic',
					value: !item.italic,
				})
			"
		>
			<v-icon>mdi-format-italic</v-icon>
		</v-btn>

		<!-- font color -->
		<v-menu
			top
			:close-on-content-click="false"
			offset-y
			v-if="isPropertyExist('color')"
		>
			<template v-slot:activator="{ on, attrs }">
				<v-btn color="white" v-bind="attrs" v-on="on">
					<div
						class="title"
						:style="{
							borderBottom: `3px solid ${item.color}`,
							height: '32px',
						}"
					>
						A
					</div>
				</v-btn>
			</template>
			<v-card width="100" align="center">
				<v-card-text class="px-1">
					<v-icon
						v-for="(hex_value, index) in colors_array"
						:key="index"
						:color="hex_value"
						:class="{
							'highlight-class-wr': item.color == hex_value,
							'cursor-wr': true,
						}"
						@click="
							$emit('update-style', {
								attribute: 'color',
								value: hex_value,
							})
						"
						>mdi-checkbox-blank</v-icon
					>
				</v-card-text>
			</v-card>
		</v-menu>
	</v-btn-toggle>
</template>

<script>
export default {
	name: "FeaturesBar",

	props: {
		item: {
			required: true,
			type: Object,
		},
		colors_array: {
			required: true,
			type: Array,
		},
	},

	data() {
		return {
			font_sizes: [
				"subtitle-1",
				"subtitle-2",
				"body-1",
				"body-2",
				"button",
				"caption",
				"overline",
			],

			font_families: [
				"serif",
				"sans-serif",
				"monospace",
				"cursive",
				"fantasy",
				"system-ui",
				"ui-serif",
				"ui-sans-serif",
				"ui-monospace",
				"ui-rounded",
				"emoji",
				"math",
				"fangsong",
			],
		};
	},

	methods: {
		isPropertyExist(property) {
			return this.item.hasOwnProperty(property);
		},
	},
};
</script>

<style scoped>
.highlight-class-wr {
	border: 1px solid black;
}
.cursor-wr {
	cursor: pointer;
}
</style>
