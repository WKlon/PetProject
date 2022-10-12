<template lang="">
	<div class="word_form">
		<form @submit.prevent>
			<h4>Making a new couple of words</h4>
			<label class="text-field__label">Word</label>
			<DefInput v-model="couple.new_word" type="text" placeholder="NewWord" />
			<label class="text-field__label">Translate</label>
			<DefInput
				v-model="couple.translate"
				type="text"
				placeholder="Translate"
			/>
			<DefButton class="btn" @click="addCouple">Add</DefButton>
		</form>
	</div>
</template>
<script>
	export default {
		data() {
			return {
				couple: {
					id: "",
					new_word: "",
					translate: "",
				},
			};
		},
		methods: {
			addCouple() {
				this.couple.id = Date.now();
				this.$emit("create", this.couple);
				this.couple = {
					new_word: "",
					translate: "",
				};
			},
		},
	};
</script>
<style scoped>
	.word_form {
		display: flex;
		flex-direction: column;
	}
	.btn {
		margin-top: 10px;
		align-self: flex-end;
		width: 100%;
	}
	h4 {
		text-align: center;
	}
</style>
