<template>
    <div>
      <h1>My Todos</h1>
      <div class="mb-2">
        <v-text-field v-model="search" label="Search Todos"></v-text-field>
      </div>
      <div class="mb-2">
        <v-select v-model="filter" label="Filter by status" :items="filters"></v-select>
      </div>
      <div class="mb-2">
        <v-text-field v-model="Add" label="Add Todos"></v-text-field>
      </div>
      <v-data-table :headers="headers" :items="todos" :search="search" :loading="loading">
        <template v-slot:item.action="{ item }">
            <v-icon small @click="editTodoDialog = true">mdi-pencil</v-icon>
                      <v-btn color="success" v-if="item.status === 'pending'" @click="markDone(item)">Mark Done</v-btn>
          <v-btn color="warning" v-if="item.status === 'done'" @click="markUndone(item)">Mark Undone</v-btn>
          <v-btn color="error" @click="deleteItem(item)">Delete</v-btn>
        </template>
      </v-data-table>
    </div>
  </template>
  
  <script>

  export default {
    name: 'TodosPage',
    data() {
      return {
        headers: [
          { text: 'Title', value: 'title' },
          { text: 'Description', value: 'description' },
          { text: 'Status', value: 'status' },
          { text: 'Action', value: 'action' },
  ],
  todos: [
    { id: 1, title: 'Todo 1', description: 'Description for Todo 1', status: 'pending', owner: 'user1' },
    { id: 2, title: 'Todo 2', description: 'Description for Todo 2', status: 'done', owner: 'user2' },
    { id: 3, title: 'Todo 3', description: 'Description for Todo 3', status: 'pending', owner: 'user3' },
    { id: 4, title: 'Todo 4', description: 'Description for Todo 4', status: 'done', owner: 'user1' },
    { id: 5, title: 'Todo 5', description: 'Description for Todo 5', status: 'pending', owner: 'user2' },
  ],
  loading: false,
  search: '',
  filter: '',
}
},
computed: {
filters() {
const statuses = new Set(this.todos.map(todo => todo.status))
return ['All', ...statuses]
},
filteredTodos() {
let filtered = this.todos.filter(todo => todo.owner === this.$store.state.user)
if (this.filter !== 'All') {
filtered = filtered.filter(todo => todo.status === this.filter)
}
return filtered
},
},
methods: {
markDone(item) {
this.loading = true
setTimeout(() => {
item.status = 'done'
this.loading = false
}, 1000)
},
markUndone(item) {
this.loading = true
setTimeout(() => {
item.status = 'pending'
this.loading = false
}, 1000)
},
deleteItem(item) {
this.loading = true
setTimeout(() => {
this.todos = this.todos.filter(todo => todo.id !== item.id)
this.loading = false
}, 1000)
},
}
}

</script>


  
