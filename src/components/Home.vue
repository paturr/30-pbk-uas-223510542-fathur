<template>
  <div class="home-container">
    <div class="home-content">
      <h1 class="home-title">Jasa Laundry Berkah</h1>
      <p class="home-description">TUGAS UAS PBK FATHUR AZRAHMAN</p>
      <router-link to="/about" class="btn" @click="handleAboutClick">⇨ TOKO KAMI !! ⇦</router-link>
    </div>
    <div class="side-feature">
      <h2 class="feature-title">Promo Grand Opening</h2>
      <p class="feature-description">Dapatkan promo besar-besaran di toko kami, ingat promo terbatas!!</p>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    handleAboutClick() {
      this.$router.push('/about');
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body {
  font-family: 'Roboto', sans-serif;
}

.home-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(to right, rgba(15, 12, 41, 0.8), rgba(48, 43, 99, 0.8), rgba(36, 36, 62, 0.8)), 
 
}

.home-content {
  text-align: center;
  background-color: rgba(255, 255, 255, 0.9);
  padding: 40px;
  border-radius: 20px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  margin-right: 40px;
  backdrop-filter: blur(10px);
  color: #333;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.home-content:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.4);
}

.home-title {
  font-size: 48px;
  font-weight: bold;
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.home-description {
  font-size: 20px;
  color: #666;
  margin-bottom: 30px;
}

.btn {
  padding: 15px 30px;
  background-color: #007bff;
  color: white;
  text-decoration: none;
  border-radius: 25px;
  font-size: 18px;
  transition: background-color 0.3s ease, transform 0.3s ease;
  display: inline-block;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.btn:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

.side-feature {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.9);
  border-radius: 20px;
  padding: 30px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(10px);
  width: 250px;
  text-align: center;
  color: #333;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.side-feature:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.4);
}

.feature-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 15px;
}

.feature-description {
  font-size: 16px;
  color: #666;
  margin-bottom: 20px;
}

.feature-image {
  width: 150px;
  height: auto;
  margin-top: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.feature-image:hover {
  transform: scale(1.1);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

@media (max-width: 768px) {
  .home-container {
    flex-direction: column;
  }

  .home-content {
    margin-right: 0;
    margin-bottom: 20px;
  }

  .side-feature {
    margin-top: 20px;
    margin-left: 0;
  }
}
</style>
