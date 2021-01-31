<template>
	<div id="current-todos" class="container">
		<h3 v-if="todos.length > 0">Задачи на выполнение: {{todos.length}}</h3>

		<ul class="ct--lists">
			<li class="ct--list" v-for="(todo, index) in todos" :key="index">
				<div class="ct--list-title">{{todo.body}}</div>

				<div class="ct--buttons">
					<button type="button" @click="edit(todo)">
						<i class="material-icons">create</i>
					</button>
					<button type="button" @click="complete(todo)">
						<i class="material-icons">check</i>
					</button>
					<button type="button" @click="remove(todo)">
						<i class="material-icons">delete</i>
					</button>
				</div>
			</li>
		</ul>

	</div>
</template>

<script>
	export default {
		methods: {
			edit(todo){
				this.$store.dispatch('editTodo', todo)
			},
			complete(todo){
				this.$store.dispatch('completeTodo', todo)
			},
			remove(todo){
				this.$store.dispatch('removeTodo', todo)
			}
		},
		computed: {
			todos(){
				return this.$store.getters.todos
			}
		}
	}
</script>