<template>
	<div id="app">

		<div class="header-div">
			<h1 class="ui header">
				<span>VueJS Todo App</span>
				<div class="sub header"> Completed Todos: {{todos.filter((todo) => { return todo.done == true }).length}} </div>
				<div class="sub header"> InCompleted Todos: {{todos.filter((todo) => { return todo.done != true }).length}} </div>
			</h1>
		</div>

		<create-todo @create-todo="addTodo"></create-todo>
		<todo-list :todos="todos"></todo-list>

	</div>
</template>

<script>
import TodoList from '@/components/TodoList';
import CreateTodo from '@/components/CreateTodo';

export default {
	name: 'app',

	created() {
		this.$on('create-todo', (data) => {
			console.log(data);
		})
	},

	data() {
		return {
			todos: [
				{
					title: 'A',
					project: 'Description A',
					done: false
				},
				{
					title: 'B',
					project: 'Description B',
					done: false
				},
				{
					title: 'C',
					project: 'Description C',
					done: false
				}
			]
		}
	},

	methods: {
		addTodo(todo) {
			this.todos.push({
				title: todo.title,
				project: todo.project,
				done: todo.done
			});
		}
	},

	components: {
		TodoList,
		CreateTodo
	}
}
</script>

<style>
#app {
	
}

.header-div {
	display: flex;
	justify-content: center;
}

.header-div span {
	border-bottom: solid 1.5px #000;
}

.sub.header {
	text-align: center;
}

</style>
