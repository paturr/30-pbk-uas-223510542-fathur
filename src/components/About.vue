<template>
  <div class="about-container">
    <div class="about-content">
      <h1 class="about-title">Jasa Lundry Berkah </h1>
      <p class="about-description">Jasa laundry berkah kini telah memiliki cabang baru. Kini jasa laundry bberkah telah ada di marpoyan tepatnya di Jl. Karya 1, belakang kampus UIR. Kini mahasiswa UIR terkhusus yang tinggal di Jl. Karya 1 tidak perlu jauh jauh mengantarkan baju nya ke laundry yang jauh. Mari laundry di jasa laundry berkah di jamin bersih, wangi dan liicin.</p>
      
      <div class="feature-boxes">
        <div class="feature-box">
          <h2 class="box-title">Jasa Lundry Berkah</h2>
          <p class="box-description">Kini kami hadir bukan hanya menerima cucian baju, tapi kini kami hadir membantu meringankan kesibukan anda dengan cara siap menerima laundry baju, celana, sepatu, spray, selimut, helm dan lain lain, .</p>
        </div>
        <div class="feature-box">
          <h2 class="box-title">Grand Opening</h2>
          <p class="box-description">Hadirilah grand opening toko kami pada hari minggu dari pukul 09.00- 16.30 WIB. Jangan sampai ketinggalan!!.</p>
        </div>
        <div class="feature-box">
          <h2 class="box-title">Mau santai di rumah? Jasa laundryin aja!!</h2>
          <div class="image-container">
            <img src="https://png.pngtree.com/png-clipart/20220705/original/pngtree-washing-machine-and-laundry-png-image_8322255.png" alt="ALL NEW NMAX" class="box-image">
            <img src="https://3.bp.blogspot.com/-y3rkBW530gE/WvF5bM3MA9I/AAAAAAAAFrk/zHJXTp4iFycXAHJehZSDCdqsaOXA_tl_ACLcBGAs/s1600/1.png" alt="ALL NEW NMAX" class="box-image">
            <img src="https://banner2.cleanpng.com/20180328/epe/kisspng-laundry-detergent-washing-machines-clip-art-laundry-5abb4467bfd615.6266765615222221837858.jpg" alt="ALL NEW NMAX" class="box-image">
          </div>
        </div>
      </div>
      
      <p class="about-contact">CP :WA: 08123456789</p>
    </div>
  </div>
</template>

<script>
export default {

}
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

.about-container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url();
  background-size: cover;
  background-position: center;
  padding: 20px;
}

.about-content {
  text-align: center;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s, transform 0.5s;
  padding: 30px;
  max-width: 900px;
  margin: 0 auto;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

.about-container:hover .about-content {
  opacity: 1;
  transform: translateY(0);
}

.about-title {
  font-size: 36px;
  font-weight: bold;
  color: #050505;
  margin-bottom: 20px;
}

.about-description {
  font-size: 18px;
  color: #fdfcfc;
  margin-bottom: 30px;
  text-align: justify;
}

.feature-boxes {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.feature-box {
  background-color: rgba(255, 255, 255, 0.9);
  border-radius: 10px;
  padding: 20px;
  margin: 10px;
  width: 280px;
  text-align: center;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.box-title {
  font-size: 20px;
  font-weight: bold;
  color: #333;
  margin-bottom: 10px;
}

.box-description {
  font-size: 16px;
  color: #666;
  text-align: left; /* Left align for better readability */
}

.image-container {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.box-image {
  width: 100%;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.about-contact {
  font-size: 18px;
  color: #fdfcfc;
  margin-top: 30px;
}

@media (max-width: 768px) {
  .about-content {
    padding: 20px;
  }

  .feature-boxes {
    flex-direction: column;
    align-items: center;
  }

  .feature-box {
    width: 100%;
  }
}
</style>
