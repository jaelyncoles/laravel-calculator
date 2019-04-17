<template>
	<div>
		<div id="whole">
			<div id="output">
				<h2>{{getOutput}}</h2>
			</div>
			<div class="row">
				<div class="col-4" v-for="button in buttons" :key="button.id">
					<numbutComponent
						v-bind:numbutid="button.id"
						v-bind:numbutvalue="button.value"
						v-on:onClickedButton="updateOutput"
					></numbutComponent>
				</div>
			</div>
			<div id="extra">
				<button id="clear" size="lg" @click="clearAll()">C</button>
				<button id="equal" size="lg" @click="evalAll()">=</button>
			</div>
		</div>
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
					{ id: 0, value: "0" },
					{ id: 1, value: "1" },
					{ id: 2, value: "2" },
					{ id: 3, value: "3" },
					{ id: 4, value: "4" },
					{ id: 5, value: "5" },
					{ id: 6, value: "6" },
					{ id: 7, value: "7" },
					{ id: 8, value: "8" },
					{ id: 9, value: "9" },
					{ id: 10, value: "+" },
					{ id: 11, value: "*" },
					{ id: 12, value: "-" },
					{ id: 13, value: "/" }
				],
				output: []
			};
		},
		components: {
			numbutComponent
		},
		methods: {
			clearAll: function() {
				// clear button
				this.output = [];
			},
			updateOutput: function(obj) {
				console.log(obj);
				var num = this.isnumber(obj.value);
				console.log(num);
				this.output.push(num);
			},
			isnumber(num) {
				// if is not a number: +, -, *, /
				// return
				if (isNaN(num) == false) {
					return parseInt(num);
				}
				return num;
			}
		},
		computed: {
			getOutput() {
				return this.output.join("");
			},

			evalAll() {
				var val = eval(this.output.join(""));
				this.output = [];
				this.updateOutput({ value: val });
			}
		},
		created() {
			console.log("we are in the calcc comp now");
		}
	};
</script>
<style scoped>
	#output {
		border: 1px solid black;
		height: 35px;
		margin: 30px;
	}

	#whole {
		border: 2px solid black;
		height: 50%;
		width: 25%;
		margin-left: 35%;
		margin-top: 20%;
	}

	#extra {
		text-align: right;
		padding-right: 5%;
		padding-bottom: 10%;
	}
</style>