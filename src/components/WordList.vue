<template>
	<div v-if="words.length > 0">
		<transition-group name="word-list">
			<CoupleItem
				v-for="word in words"
				:word="word"
				:key="word.id"
				@remove="$emit('remove', word)"
			/>
		</transition-group>
	</div>
	<h2 v-else style="color: red">Error, the array of words are emply</h2>
</template>
<script>
	import CoupleItem from "./CoupleItem.vue";
	export default {
		components: {
			CoupleItem,
		},
		props: {
			words: {
				type: Array,
				required: true,
			},
		},
	};
</script>
<style>
	.word-list {
		display: inline-block;
		margin-right: 10px;
	}
	.word-list-active,
	.word-list-active {
		transition: all 1s ease;
	}
	.word-list-from,
	.word-list-to {
		opacity: 0;
		transform: translateY(30px);
	}
</style>
