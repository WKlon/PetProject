<template>
	<div>
		<select v-model="modelValue" @change="changeOption">
			<option disabled value="">Choise from list</option>
			<option
				v-for="option in options"
				:key="option.value"
				:value="option.value"
			>
				{{ option.name }}
			</option>
		</select>
	</div>
</template>
<script>
	export default {
		name: "DefSelect",
		props: {
			modelValue: {
				type: String,
			},
			options: {
				type: Array,
				default: () => [],
			},
		},
		methods: {
			changeOption(event) {
				this.$emit("update:modelValue", event.target.value);
			},
		},
	};
</script>
<style lang=""></style>
