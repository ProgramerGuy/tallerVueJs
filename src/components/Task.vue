<template>
	<div @dblclick="succesTask" @click="selectedItem(task)" class="task-component container">
		<div class="card">
			<div class="card-image">
				<figure class="image task-image">
					<img :src="image">
				</figure>
			</div>
			<div class="card-content">
				<span class="title is-4">
					{{ task.name }}
				</span>
			</div>
		</div>
	</div>
</template>

<script type="text/javascript">
	import Vue from 'vue'

	var imgs = require.context("../assets/", false,/\.png$/);

	window.bus = new Vue({});
	
	export default{
		props: ["task"],
		data(){
			return{
				isSuccess: false,
			}
		},
		methods: {
			selectedItem: function(item){
				bus.$emit("selectedItem",item);
				bus.$emit("isSuccess",false)
			},
			succesTask: function(){
				this.isSuccess = true;
				bus.$emit("isSuccess",true)
			}
		},
		computed: {
			image: function(){
				//return "../assets/icon-1@2x.png"
				if(this.isSuccess)
					return imgs("./icon-done.png")
				else
					return imgs('./icon-1.png')
			}
		}
	}
</script>

<style type="text/css">
	.task-image img{
		margin-left: auto;
		margin-right: auto;
		width: 80px;
		height: 100px;
	}

	.task-image{
		padding-top: 40px;
	}

	.task-component{
		width: 200px;
	}
</style>