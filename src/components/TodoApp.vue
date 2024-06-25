<template>
  <div class="todo-app">
    <header>
      <nav>
        <ul>
          <li @click="activeTab = 'todos'" :class="{ active: activeTab === 'todos' }">Todos</li>
          <li @click="activeTab = 'posts'" :class="{ active: activeTab === 'posts' }">Post</li>
        </ul>
      </nav>
    </header>

    <TodoList v-if="activeTab === 'todos'"
              :todos="todos"
              :filter="filter"
              :newTodo="newTodo"
              @addTodo="addTodo"
              @removeTodo="removeTodo"
              @update:newTodo="updateNewTodo" />

    <div v-else-if="activeTab === 'posts'" class="posts">
      <h1>Postingan User</h1>
      <select v-model="selectedUser" @change="fetchPosts">
        <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
      </select>
      <div v-if="loading" class="loading">Loading...</div>
      <ul v-else-if="filteredPosts.length > 0">
        <li v-for="post in filteredPosts" :key="post.id">
          <h2>{{ post.title }}</h2>
          <p class="post-body">{{ post.body }}</p>
        </li>
      </ul>
      <p v-else>Tidak ada postingan untuk user yang dipilih.</p>
    </div>
  </div>
</template>

<script>
import TodoList from './TodoList.vue';

export default {
  components: {
    TodoList
  },
  data() {
    return {
      activeTab: 'todos',
      newTodo: '',
      todos: [],
      filter: 'all', // 'all', 'done', 'pending'
      users: [],
      posts: [],
      selectedUser: null,
      loading: false
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          text: this.newTodo,
          done: false,
        });
        this.newTodo = ''; // Reset input field
        this.saveTodos();
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
      this.saveTodos();
    },
    saveTodos() {
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
    loadTodos() {
      const savedTodos = localStorage.getItem('todos');
      if (savedTodos) {
        this.todos = JSON.parse(savedTodos);
      }
    },
    async fetchPosts() {
      try {
        this.loading = true;
        const response = await fetch('https://jsonplaceholder.typicode.com/posts');
        if (!response.ok) throw new Error('Network response was not ok');
        this.posts = await response.json();
      } catch (error) {
        console.error('There was a problem with the fetch operation:', error);
      } finally {
        this.loading = false;
      }
    },
    async fetchUsers() {
      try {
        this.loading = true;
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        if (!response.ok) throw new Error('Network response was not ok');
        this.users = await response.json();
      } catch (error) {
        console.error('There was a problem with the fetch operation:', error);
      } finally {
        this.loading = false;
      }
    },
    updateNewTodo(newTodo) {
      this.newTodo = newTodo;
    }
  },
  created() {
    this.fetchUsers();
    this.loadTodos();
  },
  watch: {
    selectedUser(newVal) {
      if (newVal) {
        this.fetchPosts();
      }
    }
  },
  computed: {
    filteredPosts() {
      if (this.selectedUser) {
        return this.posts.filter(post => post.userId === this.selectedUser);
      } else {
        return [];
      }
    }
  }
};
</script>

<style scoped>
/* Your scoped CSS styles here */
</style>
