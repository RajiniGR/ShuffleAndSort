<template>
	<div class="headertext p-3 text-center"><b>{{ HeaderText }}</b></div>
	<div>
		<b-row>
			<b-col class="ml-md-auto p-3 cal-btn">
				<b-row v-for="(group, i) in articleGroups" :key="i">
					<b-col>
						<button  v-for="(x, key) in expression.slice(i * itemsPerRow, (i + 1) * itemsPerRow)" :key="key" type="button">{{x}}</button>
					</b-col>
				</b-row>
			</b-col>
			
			<b-col class="ml-md-auto p-3 action-btn">
				<div>
					<b-button  md="2" type="button" size="sm" lg="4" class="pb-2" variant="" @click.stop="randomNumber()">Shuffle</b-button>
				</div>
				<div class="pt-2">
					<b-button  md="2" type="button" size="sm" lg="4" class="pb-2" variant="" @click.stop="sortorder()">Sort</b-button>
				</div>
			</b-col>				
		</b-row>
	</div>
</template>

<script>

export default {
	name: "App",
	data() {
		return {
			itemsPerRow: 3,
			expression: [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ],
			HeaderText: "Shuffle and Sort"
		};
	},
	computed: {
		articleGroups () {
			return Array.from(Array(Math.ceil(this.expression.length / this.itemsPerRow)).keys())
		}
	},
	methods : {
		randomNumber : function(){
			return this.expression.sort(function(){ return 0.5 - Math.random()});
		},
		sortorder : async function(){
			return this.expression.sort()
		}
	}
};
</script>

<style scoped>
	.headertext{
		color: #333333;
	}
	@media only screen and (max-width: 375px) {
		.headertext{
			background-color: #333333;
			color: #FFFFFF;
		}
	}
	.action-btn button{
		background-color: #72C3DC;
		color: #FFFFFF;
		width: 100px;
		height: 30px;
	}
	.cal-btn button {
		width: 120px;
		height: 120px;
	}

	#clear-button {
		width: 50px;
	}

	.cal-btn button:nth-child(1) {
		background-color: #6F98A8;
	}

	.cal-btn button:nth-child(2) {
		background-color: #2B8AAD;
	}

	.cal-btn button:nth-child(3) {
		background-color: #BFBFBF;
	}
	.cal-btn button:nth-child(6), .cal-btn button:nth-child(7) {
		background-color: #EFEFEF;
	}
</style>