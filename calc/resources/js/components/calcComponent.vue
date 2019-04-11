<template>
	<div>

			<div id="output">
				<h2>{{outputnumbutvalue}}</h2>
                </div>
                <div class="row">
				<div class="col-4" v-for="button in buttons" :key="button.id">
					<numbutComponent
						v-bind:numbutid="button.id"
						v-bind:numbutvalue="button.value"
						v-on:onClickedButton="outputnumbutValue"
					></numbutComponent>
				</div>
                </div>
                <button id="clear" size="lg" @click="clearAll()">C</button>
			</div>

</template>

<script>
	//create a grid for the buttons with div for view
	//make function that emits which button clicked to the
	//create string that eval joinby
	//create a clear button that resets the div
	

	import numbutComponent from "./numbutComponent";

	export default {
		name: "calc-component",
		data() {
			return {
				buttons: [
					{ id: 0, value: 0 },
					{ id: 1, value: 1 },
					{ id: 2, value: 2 },
					{ id: 3, value: 3 },
					{ id: 4, value: 4 },
					{ id: 5, value: 5 },
					{ id: 6, value: 6 },
					{ id: 7, value: 7 },
					{ id: 8, value: 8 },
					{ id: 9, value: 9 },
					{ id: 10, value: 10 },
					{ id: 11, value: "+" },
					{ id: 12, value: "*" },
					{ id: 13, value: "-" },
					{ id: 14, value: "/" }
				],
				outputnumbutvalue: "                 "
			};
		},
		components: {
			numbutComponent
		},
		methods: {
			clearAll() {
				// clear button
				this.output.value = "";
			}
		},
		computed: {
			
			
        },
        created() {
            console.log("we are in the calcc comp now");
        }
	};
</script>
