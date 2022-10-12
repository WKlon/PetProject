<template>
	<div class="couple">
		<div>
			<div><strong>Word:</strong>{{ word.new_word }}</div>
			<div><strong>Translate:</strong>{{ word.translate }}</div>
		</div>
		<DefButton class="btn" @click="$emit('remove', word)">Delete</DefButton>
	</div>
</template>
<script>
	import DefButton from "./UI/DefButton.vue";
	export default {
		components: {
			DefButton,
		},
		props: {
			word: {
				type: Object,
				required: true,
			},
		},
	};
</script>
<style scoped>
	.couple {
		display: flex;
		border: 2px solid green;
		border-radius: 5px;
		padding: 5px;
		margin-top: 10px;
		justify-content: space-between;
	}
	.btn {
		align-self: center;
	}
</style>
