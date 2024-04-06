<template>
    <div class="profile">
        <img src="./icons/profile.png" />
        <p v-if="showTypingAnimation" class="center">{{ typedText }}</p>
    </div>
</template>

<script>
export default {
  data() {
    return {
      typedText: '',
      typingSpeed: 150,
      showTypingAnimation: false,
      paragraphText: "Alfi CHANDRA DINATA"
    };
  },
  mounted() {
    this.$nextTick(() => {
      setTimeout(() => {
        this.startTypingAnimation();
      }, 2000); // Menunda 2 detik sebelum memulai animasi pengetikan
    });
  },
  methods: {
    startTypingAnimation() {
      this.showTypingAnimation = true;
      this.typeText(this.paragraphText);
    },
    typeText(fullText) {
      let currentIndex = 0;

      const typeNextCharacter = () => {
        if (currentIndex < fullText.length) {
          this.typedText += fullText[currentIndex];
          currentIndex++;
          setTimeout(typeNextCharacter, this.typingSpeed);
        }
      };

      typeNextCharacter();
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.cdnfonts.com/css/font');
.profile {
    display: flex;
    position: fixed;
    align-items: center;
    margin-left: -50%; 
    margin-top: -80px;
    z-index: 100;
}

.profile img {
    width: 400px;
    height: auto;
    overflow: hidden;
    position: fixed;
    z-index: 1000;
    transform: scale(-1, 1);
}

.center {
    text-align: center;
    z-index: 11;
    transform: translate(50%, -50%);
    
}
p{
    font-size:12px;
    font-family: 'Font', sans-serif;
    font-weight: bold;
    position: fixed;
    margin: 0;
    width: 50%;
    margin-left: -35%;
    margin-top: -15%;
    height: auto;
    z-index: 1000; 
    color: darkcyan;
    text-shadow:    0 0 10px black,
                    0 0 20px white;
}
</style>
