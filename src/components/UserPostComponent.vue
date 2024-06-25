<template>
    <div>
      <!-- User Selector -->
      <select v-model="selectedUser" @change="changeUser" class="form-select mt-3">
        <option value="" disabled selected>Pilih pengguna</option>
        <option
          v-for="user in users"
          :key="user.id"
          :value="user.id"
        >{{ user.name }}</option>
      </select>
  
      <!-- Post List -->
      <div v-if="posts.length > 0">
        <h3 class="mb-3 fw-bold">Posts</h3>
        <ul class="list-group">
          <li
            v-for="(post, index) in posts"
            :key="index"
            class="list-group-item"
          >
            <h5 class="card-title">{{ post.title }}</h5>
            <p class="card-text">{{ post.body }}</p>
          </li>
        </ul>
      </div>
      <div v-else>
        <p>No posts available.</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      users: Array,
      posts: Array,
    },
    data() {
      return {
        selectedUser: null,
      };
    },
    methods: {
      changeUser() {
        this.$emit('select-user', this.selectedUser);
      },
    },
  };
  </script>
  