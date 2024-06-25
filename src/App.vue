<template>
  <div>
    <header class="header">
      <nav class="menu">
        <ul>
          <li><router-link to="/">🏠 Home</router-link></li>
          <li><router-link to="/todos">📝 Todos</router-link></li>
          <li><router-link to="/posts">✉️ Posts</router-link></li>
          <li><router-link to="/albums">📷 Albums</router-link></li>
          <li><router-link to="/about">ℹ️ About</router-link></li>
        </ul>
      </nav>
    </header>
    <router-view></router-view>
  </div>
</template>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(to right, #f0f4f8, #d9e2ec);
}

.header {
  background-color: #000000;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px 0;
}

.menu ul {
  display: flex;
  justify-content: center;
  list-style: none;
  padding: 0;
  margin: 0;
}

.menu ul li {
  margin: 0 20px;
}

.menu ul li a {
  text-decoration: none;
  color: #ffffff;
  font-weight: bold;
  font-size: 24px;
  padding: 10px 20px;
  transition: background-color 0.3s, transform 0.3s, box-shadow 0.3s;
  border-radius: 5px;
  text-transform: capitalize;
}

.menu ul li a:hover {
  background-color: #ff0000;
  transform: scale(1.1);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

.menu ul li a:active {
  background-color: #ff0000;
  transform: scale(1.05);
}
</style>