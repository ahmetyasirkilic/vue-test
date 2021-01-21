<template>
	<div class="search">
		<input type="text" v-model="query" @keypress.enter="handleSearch">
		<button @click="handleSearch">Search</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				query: ''
			}
		},
		methods:{
			handleSearch(){
				this.$emit('SearchRequested', this.query);
			}
		}
	}
</script>

<style>
	.search input{
		padding: 10px 20px;
		border: 1px solid #ccc;
		border-radius: 5px;
		width: 250px;
	}
	.search button{
		padding: 10px 10px;
		border: 1px solid #ccc;
		border-radius: 5px;
		color: #fff;
		background-color: #4183c4;
		font-size: 15px;
	}
</style>