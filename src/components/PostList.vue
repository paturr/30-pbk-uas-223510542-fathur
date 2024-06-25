<template>
  <section class="post-section">
    <h2 style="color: white;">Postingan Pengguna</h2>
    <div class="select-user">
      <label style="color: black;">Pilih Pengguna:</label>
      <select v-model="selectedUser" @change="fetchPosts" class="select-box">
        <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
      </select>
    </div>
    <div v-if="posts.length > 0" class="user-posts">
      <h3 style="color: black;">Postingan Pengguna: {{ selectedUserName }}</h3>
      <table class="post-table">
        <thead>
          <tr>
            <th>Judul</th>
            <th>Isi</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="post in posts" :key="post.id">
            <td>{{ post.title }}</td>
            <td>{{ post.body }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </section>

</template>

<script setup>
import { ref, onMounted } from 'vue'

const selectedUser = ref(null)
const users = ref([])
const posts = ref([])
const selectedUserName = ref('')

const fetchUsers = async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    users.value = await response.json()
  } catch (error) {
    console.error('Error fetching users:', error)
  }
}

const fetchPosts = async () => {
  if (!selectedUser.value) return
  try {
    const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${selectedUser.value}`)
    posts.value = await response.json()
    selectedUserName.value = users.value.find(user => user.id === selectedUser.value)?.name || ''
  } catch (error) {
    console.error('Error fetching posts:', error)
  }
}

onMounted(fetchUsers)
</script>

<style scoped>
.post-section {
  margin-top: 20px;
}

.select-user {
  margin-bottom: 20px;
}

.select-box {
  padding: 8px 12px;
  font-size: 16px;
  border: 1px solid #000000;
  border-radius: 5px;
  background-color: #ffffff;
  transition: border-color 0.3s, background-color 0.3s;
}

.select-box:focus {
  outline: none;
  border-color: #007bff;
  background-color: rgb(0, 0, 0);
}

.user-posts {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.post-table {
  width: 100%;
  border-collapse: collapse;
}

.post-table th,
.post-table td {
  padding: 12px;
  border: 1px solid #000000;
}

.post-table th {
  background-color: #ffffff;
}

.post-table td {
  background-color: white;
}

.post-table tr:hover {
  background-color: #000000;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: url('https://fiverr-res.cloudinary.com/images/q_auto,f_auto/gigs/129325364/original/afaddcb9d7dfaaf5bff7ef04101935814665ac16/design-an-attractive-background-for-your-website.png');
  background-size: cover;
  background-position: center;
}

img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1; 
}

h2, h3, h4, label {
  color: rgb(255, 255, 255);
}

.select-box {
  /* Menambahkan animasi pada pilihan pengguna */
  transition: background-color 0.3s, transform 0.3s;
}

.select-box:hover {
  background-color: #f0f0f0;
}

.select-box:focus {
  outline: none;
  background-color: white;
  border-color: #007bff;
}
</style>