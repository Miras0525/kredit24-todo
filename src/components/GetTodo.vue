<template>
	<div id="get-todo" class="container">
		<input
			:value="newTodo"
			@change="getTodo"
			placeholder="Напишите задачу"
		>

		<button @click="addTodo">
			<i class="material-icons">add</i>
		</button>
	</div>
</template>

<style lang="scss" scoped>
	#get-todo  {
		background: #fff;
		border-radius: 4px;
		box-shadow: 0px 1px 4px rgba(0, 0, 0, 0.01), 0px 4px 8px rgba(0, 0, 0, 0.02), 0px 1px 12px rgba(0, 0, 0, 0.12);
		padding: 12px;
		display: flex;
		align-items: center;

		& input {
			border: none;
			outline: none;
			flex-grow: 1;
		}
	}
</style>

<script>
	export default {
		methods: {
			getTodo(e){
				this.$store.dispatch('getTodo', e.target.value)
			},
			addTodo(){
				this.$store.dispatch('addTodo')
				this.$store.dispatch('clearTodo')
			}
		},
		computed: {
			newTodo(){
				return this.$store.getters.newTodo
			}
		}
	}
</script>