<template>
	<button class="btn">
		<slot></slot>
	</button>
</template>
<script>
	export default {
		name: "DefButton",
	};
</script>
<style scoped>
	.btn {
		color: black;
		border: 2px solid darkgreen;
		border-radius: 10px;
		text-transform: uppercase;
		padding: 5px;
	}
</style>
