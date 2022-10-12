<template>
	<div class="main">
		<h2>Page with words</h2>
		<div class="create_btn">
			<DefButton @click="showDialog">Create a new couple</DefButton>
			<DefSelect :options="sortOptions" v-model="selectedSort"></DefSelect>
		</div>

		<MyDialog v-model:show="dialogVisible">
			<WordForm @create="addCouple" />
		</MyDialog>
		<WordList
			v-if="isWordsLoading == true"
			:words="sortedWords"
			@remove="removeWord"
		/>
		<div v-else-if="isWordsLoading == false">
			Loading conpliting, wait a moment
		</div>
	</div>
</template>
<script>
	import WordForm from "./components/WordForm.vue";
	import WordList from "./components/WordList.vue";
	import DefButton from "./components/UI/DefButton.vue";
	import DefSelect from "./components/UI/DefSelect.vue";
	export default {
		components: {
			WordForm,
			WordList,
			DefButton,
			DefSelect,
		},
		data() {
			return {
				words: [],
				dialogVisible: false,
				isWordsLoading: false,
				selectedSort: "",
				sortOptions: [
					{ value: "new_word", name: "on words" },
					{ value: "translate", name: "on translates" },
				],
			};
		},
		methods: {
			addCouple(couple) {
				this.words.push(couple);
				this.dialogVisible = false;
			},
			removeWord(word) {
				this.words = this.words.filter((p) => p.id !== word.id);
			},
			showDialog() {
				this.dialogVisible = true;
			},
			async fetchWords() {
				try {
					fetch("https://my-json-server.typicode.com/WKlon/Worddb/words")
						.then((response) => response.json())
						.then((json) => {
							this.words = json;
							this.isWordsLoading = true;
						});
				} catch (e) {
					alert("Loading ERROR");
				} finally {
					this.isWordsLoading = false;
				}
			},
		},
		mounted() {
			this.fetchWords();
		},
		computed: {
			sortedWords() {
				return [...this.words].sort((word1, word2) => {
					return word1[this.selectedSort]?.localeCompare(
						word2[this.selectedSort]
					);
				});
			},
		},
		watch: {
			selectedSort(newValue) {
				this.words.sort((word1, word2) => {
					return word1[this.selectedSort]?.localeCompare(
						word2[this.selectedSort]
					);
				});
			},
		},
	};
</script>
<style>
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		background-color: bisque;
	}
	.main {
		padding: 10px;
		margin: auto;
		width: 70%;
	}
	.create_btn {
		display: flex;
		justify-content: space-between;
	}
</style>
