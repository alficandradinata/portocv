<template>
  <bg />

  <div class="profile">
    <pfr />
  </div>

  <div>
    <muncul />
  </div>


  <div class="icon">
    <iconSvg />
  </div>

  <div class="button">
    <tombol />
  </div>
</template>

<script>
import bg from './components/background.vue';
import pfr from './components/profile.vue';
import muncul from './components/slide.vue';
import iconSvg from './components/iconSvg.vue';
import tombol from './components/button.vue';

export default {
  name: 'App',
  components: {
    bg,
    pfr,
    muncul,
    iconSvg,
    tombol

  }
}
</script>

<style>
.profile{
  position: relative;
}
  .icon {
  display: flex;
  position: fixed;
  align-items: center;
  width: 300px;
  height: auto;
  z-index: 20;
  top: 550px;
  left: 40%;
  filter: drop-shadow(0 0 5px #000);
  overflow: hidden;
}
.icon >*{
  margin-left: 20px; 
}
</style>