<template lang="">
	<div>
		<input :value="modelValue" @input="updateInput" type="text" />
	</div>
</template>
<script>
	export default {
		name: "DefInput",
		props: {
			modelValue: [String],
		},
		methods: {
			updateInput(event) {
				this.$emit("update:modelValue", event.target.value);
			},
		},
	};
</script>
<style scoped>
	input[type="text"] {
		font-family: inherit;
		font-size: inherit;
		line-height: inherit;
		margin: 0;
		display: block;
		width: 100%;
		height: calc(2.25rem + 2px);
		padding: 0.375rem 0.75rem;
		font-family: inherit;
		font-size: 1rem;
		font-weight: 400;
		line-height: 1.5;
		color: #212529;
		background-color: #fff;
		background-clip: padding-box;
		border: 1px solid #bdbdbd;
		border-radius: 0.25rem;
		transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
	}
</style>
