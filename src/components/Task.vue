<template>
	<div @click="selectedItem(task)" class="task-component container">
		<div class="card">
			<div class="card-image">
				<figure class="image task-image">
					<img src="../assets/icon-1@2x.png">
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
	
	window.bus = new Vue({});
	
	export default{
		props: ["task"],
		methods: {
			selectedItem: function(item){
				bus.$emit("selectedItem",item);
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