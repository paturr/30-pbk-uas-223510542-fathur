<template>
  <div class="body">
    <section class="create-todo">
      <h3>Laundry Anda?</h3>
      <form @submit.prevent="addTodo">
        <h4>Masukkan barang yang ingin anda laundry</h4>
        <input type="text" placeholder="Masukkan jenis barang" v-model="inputContent" />
        <h4>Pilih jenis barang:</h4>
        <div class="options">
          <label>
            <input type="radio" name="category" value="Baju" v-model="inputCategory" />
            <span class="bubble baju"></span>
            <div>MATIC</div>
          </label>
          <label>
            <input type="radio" name="category" value="Sepatu" v-model="inputCategory" />
            <span class="bubble sepatu"></span>
            <div>SPORT</div>
          </label>
          <label>
            <input type="radio" name="category" value="Lainnya" v-model="inputCategory" />
            <span class="bubble lainnya"></span>
            <div>BEBEK</div>
          </label>
        </div>
        <button type="submit">Submit</button>
      </form>
    </section>

    <section class="todo-list">
      <table>
        <thead>
          <tr>
            <th>PRODUK</th>
            <th>Kategori</th>
            <th>Status</th>
            <th>Aksi</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="todo in todosAsc" :key="todo.createdAt" :class="`todo-item ${todo.done ? 'done' : ''}`">
            <td>{{ todo.content }}</td>
            <td>{{ todo.category }}</td>
            <td>
              <button class="status" @click="toggleDone(todo)">
                {{ todo.done ? 'READY' : 'INDENT' }}
              </button>
            </td>
            <td>
              <button class="delete" @click="removeTodo(todo)">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
    </section>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch } from 'vue'

const todos = ref([])
const inputContent = ref('')
const inputCategory = ref(null)

const todosAsc = computed(() => todos.value.slice().sort((a, b) => b.createdAt - a.createdAt))

const addTodo = () => {
  if (inputContent.value.trim() === '' || inputCategory.value === null) {
    return
  }

  todos.value.push({
    content: inputContent.value,
    category: inputCategory.value,
    done: false,
    createdAt: new Date().getTime()
  })

  inputContent.value = ''
  inputCategory.value = null
}

const removeTodo = todo => {
  todos.value = todos.value.filter(t => t !== todo)
}

const toggleDone = todo => {
  todo.done = !todo.done
}

watch(todos, newVal => {
  localStorage.setItem('todos', JSON.stringify(newVal))
}, { deep: true })

onMounted(() => {
  todos.value = JSON.parse(localStorage.getItem('todos')) || []
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body, html {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  height: 100%;
  width: 100%;
  font-family: 'Roboto', sans-serif;
}

.body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7));
  background-size: cover;
  background-position: center;
  padding: 20px;
}

.create-todo, .todo-list {
  width: 100%;
  max-width: 700px;
  margin: 20px;
  padding: 20px;
  background-color: rgba(255, 255, 255, 0.95);
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
}

.create-todo h3 {
  color: #333;
  font-size: 28px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 20px;
}

.create-todo form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.create-todo form h4 {
  font-size: 18px;
  font-weight: bold;
  margin: 10px 0;
}

.create-todo input[type="text"] {
  padding: 10px;
  width: 100%;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.create-todo .options {
  display: flex;
  justify-content: center;
  margin: 10px 0;
}

.create-todo .options label {
  display: flex;
  align-items: center;
  margin: 0 10px;
  cursor: pointer;
}

.create-todo .options input[type="radio"] {
  display: none;
}

.create-todo .options .bubble {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin-right: 10px;
  border: 2px solid transparent;
  transition: all 0.3s;
}

.create-todo .options input[type="radio"]:checked + .bubble {
  border-color: #007bff;
}

.create-todo .options .matic { background: #ffcccb; }
.create-todo .options .sport { background: #ccffcc; }
.create-todo .options .bebek { background: #ccccff; }

.create-todo button[type="submit"] {
  padding: 10px 20px;
  border: none;
  background: #007bff;
  color: white;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s;
}

.create-todo button[type="submit"]:hover {
  background: #0056b3;
}

.todo-list table {
  width: 100%;
  border-collapse: collapse;
  background-color: #fff;
  border-radius: 5px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
}

.todo-list th, .todo-list td {
  padding: 10px;
  text-align: center;
}

.todo-list th {
  background-color: #f2f2f2;
  font-weight: bold;
}

.todo-list tr:hover {
  background-color: #f5f5f5;
}

.todo-list .todo-item.done {
  background: #e0ffe0;
}

.todo-list .todo-item .status {
  padding: 8px 16px;
  border: none;
  background-color: #28a745;
  color: #fff;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.todo-list .todo-item .status:hover {
  background-color: #218838;
}

.todo-list .todo-item .delete {
  padding: 8px 16px;
  border: none;
  background-color: #dc3545;
  color: #fff;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.todo-list .todo-item .delete:hover {
  background-color: #c82333;
}

@media (max-width: 768px) {
  .create-todo, .todo-list {
    padding: 15px;
  }

  .create-todo h3 {
    font-size: 24px;
  }

  .create-todo form h4 {
    font-size: 16px;
  }

  .create-todo input[type="text"] {
    font-size: 14px;
  }

  .todo-list th, .todo-list td {
    font-size: 14px;
  }
}
</style>
