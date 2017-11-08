<template>
	<div class="task-component">
		<h1 class="title is-2">{{ task.name }}</h1>
	</div>
</template>

<script type="text/javascript">
	export default{
		props: ["task"]
	}
</script>

<style type="text/css">
	.task-component{
		background-color: red;
	}
</style>