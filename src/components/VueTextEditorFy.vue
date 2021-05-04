<template>
	<div v-if="field && field.id && field.text">
		<v-menu
			:close-on-content-click="false"
			offset-y
			:disabled="!isNoEditingOptionProvided"
		>
			<template v-slot:activator="{ on, attrs }">
				<div :id="field.id">
					<component
						:is="type"
						v-model="field.text"
						no-resize
						hide-details
						:solo="solo"
						v-on="on"
						v-bind="attrs"
						:color="isPropertyExist('background') ? field.background : 'black'"
						:background-color="
							isPropertyExist('background') ? field.background : 'white'
						"
						:class="[
							{
								'font-weight-bold': isPropertyExist('bold')
									? field.bold
									: false,
								'font-italic': isPropertyExist('italic') ? field.italic : false,
								[isPropertyExist('fontSize') ? field.fontSize : '']: true,
							},
						]"
					></component>
				</div>
			</template>

			<FeaturesBar
				:item="field"
				:colors_array="colors"
				@update-style="updateStyle(field.id, $event)"
			></FeaturesBar>
		</v-menu>
	</div>
</template>

<script>
import FeaturesBar from "@/components/FeaturesBar.vue";

export default {
	name: "VueTextEditorFy",

	data() {
		return {
			field: this.item ? this.item : null,
		};
	},

	props: {
		item: {
			type: Object,
			required: true,

			validator: function(obj) {
				return obj && obj.hasOwnProperty("id") && obj.hasOwnProperty("text");
			},
		},

		type: {
			type: String,
			default: "v-textarea",
		},

		colors: {
			type: Array,
			default: function() {
				return [
					"#F5F5F5",
					"#FFAC77",
					"#FFEB3B",
					"#CDDC39",
					"#41BBB4",
					"#FFC107",
					"#8BC34A",
					"#F587C7",
					"#FB8C01",
					"#4CAF50",
					"#2196F3",
					"#607D8B",
					"#E53935",
					"#1A76D2",
					"#E91E63",
					"#795548",
					"#9C27B0",
					"#000000",
				];
			},
		},
		solo: {
			default: false,
		},
	},

	components: {
		FeaturesBar,
	},

	mounted() {
		this.manageStyle();
	},

	computed: {
		isNoEditingOptionProvided() {
			let properties = [
				"bold",
				"italic",
				"color",
				"background",
				"fontFamily",
				"fontSize",
			];
			let count = 0;
			properties.forEach((property) => {
				if (this.isPropertyExist(property)) count++;
			});
			return count;
		},
	},

	methods: {
		isPropertyExist(property) {
			return this.field.hasOwnProperty(property);
		},

		manageStyle() {
			try {
				this.$nextTick(() => {
					if (this.isPropertyExist("color")) {
						this.updateStyle(this.field.id, {
							attribute: "color",
							value: this.field.color,
						});
					}
					if (this.isPropertyExist("fontFamily")) {
						this.updateStyle(this.field.id, {
							attribute: "fontFamily",
							value: this.field.fontFamily,
						});
					}
				});
			} catch (error) {
				console.error(error);
			}
		},

		async updateStyle(id, payload) {
			try {
				this.field[payload.attribute] = payload.value;

				// We need to assign it manually because bind style is not working in textarea.
				if (["color", "fontFamily"].includes(payload.attribute)) {
					// check type of input field
					let tagName = this.type === "v-textarea" ? "textarea" : "input";

					let parent_el = document.getElementById(id);

					// Check if parent element found
					if (parent_el) {
						let child_el = parent_el.getElementsByTagName(tagName)[0];

						// Check if respcted child element found then apply style
						if (child_el) {
							child_el.style[payload.attribute] = payload.value;
						}
					}
				}
			} catch (error) {
				console.error(error);
			}
		},
	},
};
</script>
