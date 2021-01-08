<template>
  <div class="container text-center mt-5">
    <div class="header">
      <h3>{{name}}</h3>
    </div>
    <div class="image">
      <img src="../assets/images/glitch_img.jpg" class="img-fluid" alt="glitch_img">
    </div>
    <div class="nav-section mt-4">
      <ul class="nav justify-content-center align-items-center">
        <li class="nav-item">
          <a class="nav-link" href="">HOME</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="">ABOUT</a>
        </li>
        <li class="nav-item">
          <img src="../assets/images/avatar.jpg" alt="avatar">
        </li>
        <li class="nav-item">
          <a class="nav-link" href="">GALLERY</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="">CONTACT</a>
        </li>
      </ul>
    </div>
    <div class="socials">
      <a :href="links.instagram"><i class="fab fa-instagram fa-2x"></i></a>
      <a :href="links.twitter"><i class="fab fa-twitter-square fa-2x"></i></a>
      <a :href="links.snapchat"><i class="fab fa-snapchat-square fa-2x"></i></a>
      <a :href="`mailto:${links.email}`"><i class="fas fa-envelope-square fa-2x"></i></a>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
export default {
  name: 'Home',
  data:()=>({
    name: '',
    links:''
  }),
  components: {
    
  },
  mounted() {
    axios.get('https://hirng-x2021.glitch.me/api').then(response => {
      this.name = response.data.name
      this.links = response.data.social_media
    })
  }
}
</script>
<style>
  .header h3 {
    font-size: 25px;
    color: #EEBBCD;
    letter-spacing: 10px;
    font-weight: lighter;
    padding-left: 55px;
  }
  .nav {
    padding-left: 4rem !important;
  }
  .image img {
    margin-top: 30px;
    box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
  }
  .nav-item img {
    border-radius: 50%;
    height: 70px;
    width: 70px;
  }
  .nav-link {
    color: #EEBBCD;
    letter-spacing: 5px;
    font-size: 15px;
    padding: 0.5rem 1.5rem !important;
  }
  .nav-link:hover {
    color: #fff;
  }
  .socials {
    position: absolute;
    top: 35%;
    right: 30px;
    display: flex;
    flex-direction: column;
  }
  .socials a i {
    color: #fff;
    padding: 10px;
  }
</style>
