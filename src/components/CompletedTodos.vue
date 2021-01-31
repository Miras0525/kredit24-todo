<template>
	<div id="completed-todos">
		<h3 v-if="completed.length > 0">Выполненные задачи: {{completed.length}}</h3>

		<ul class="ct--lists">
			<li 
				class="ct--list" 
				v-for="(todo, index) in completed" 
				:key="index"
			>

			<div class="ct--list-title">{{todo.body}}</div>

			<div class="ct--buttons">
				<button type="button" @click="remove(todo)">
					<i class="material-icons">delete</i>
				</button>
			</div>

			</li>
		</ul>

	</div>
</template>

<style lang="scss" scoped>
	#completed-todos {
		padding-bottom: 24px;
		margin-bottom: 24px;
		border-bottom: 2px solid;
	}
</style>

<script>
	export default {
		methods: {
			remove(todo){
				this.$store.dispatch('removeTodo', todo)
			}
		},
		computed: {
			completed(){
				return this.$store.getters.completedTodos
			}
		}
	}
</script>