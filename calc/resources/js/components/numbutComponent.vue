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
				
				
			};
		},
		methods: {
			click() {
                this.$emit("onClickedButton", { value:this.numbutvalue});
			}
		},
		computed: {
			
		}
	};
</script>