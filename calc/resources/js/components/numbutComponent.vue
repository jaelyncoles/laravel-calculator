<template>
	<div>
		<div id="button">
			<button size="lg" @click="click()">{{ numbutvalue }}</button>
		</div>
	</div>
</template>

<script>
	export default {
		name: "numbutComponent",
		props: {
			numbutid: Number,
			numbutvalue: String
		},
		data() {
			return {
				outputnumbutvalue: "",
				beenClicked: false
			};
		},
		methods: {
			click() {
				this.$emit("onClickedButton", { id: this.numbutid });
			}
		},
		computed: {
			isnumber() {
				if (isNaN(this.numbutvalue) == false) {
					this.numbutvalue = parseInt(this.numbutvalue);
				}
				return this.numbutvalue;
			}
		}
	};
</script>