<template>
  <div>
    <div class="slide-up animated" :class="{ 'slideOutDown': !showSlideUp }" v-if="showSlideUp">
      <h1 class="center">{{ slideUpText }}</h1>
    </div>
    <div v-if="showTypingAnimation">
      <p class="center">{{ typedText }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      slideUpText: 'SELAMAT DATANG DI PORTOFOLIO SAYA',
      typedText: '',
      currentIndex: 0,
      typingSpeed: 150, 
      slideUpTexts: [
        'TUGAS PERATIKUM PEMROGRAMAN BERBASIS KOMPONEN'
      ],
      showSlideUp: true,
      showTypingAnimation: false
    };
  },
  mounted() {
    this.$nextTick(() => {
      const element = this.$el.querySelector('.slide-up');
      element.classList.add('slideInUp');

      setTimeout(() => {
        this.showSlideUp = false;
        this.startTypingAnimation();
      }, 2000); 
    });
  },
  methods: {
    startTypingAnimation() {
      this.showTypingAnimation = true;
      this.typeText(this.slideUpTexts[this.currentIndex]);
    },
    typeText(fullText) {
      let currentIndex = 0;

      const typeNextCharacter = () => {
        if (currentIndex < fullText.length) {
          this.typedText += fullText[currentIndex];
          currentIndex++;
          setTimeout(typeNextCharacter, this.typingSpeed);
        } else {
          setTimeout(() => {
            // Menghapus teks satu per satu setelah pengetikan selesai
            this.deleteText();
          }, 1000); // Ubah ke 1000ms untuk menunggu sebelum menghapus teks
        }
      };

      typeNextCharacter();
    },
    deleteText() {
      let currentIndex = this.typedText.length - 1;

      const deleteNextCharacter = () => {
        if (currentIndex >= 0) {
          this.typedText = this.typedText.slice(0, currentIndex);
          currentIndex--;
          setTimeout(deleteNextCharacter, this.typingSpeed);
        } else {
          setTimeout(() => {
            this.showTypingAnimation = false;
            this.showSlideUp = true;
          }, 2000);
        }
      };

      deleteNextCharacter();
    }
  }
};
</script>

<style scoped>
@import 'animate.css/animate.css';
@import url('https://fonts.googleapis.com/css2?family=Source+Code+Pro:ital,wght@0,700;1,700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Source+Code+Pro:ital,wght@0,700;1,700&display=swap');

.slide-up {
  position: fixed;
  animation: slideInUp 2s ease;
  color: aqua;
  font-family: "Press Start 2P", system-ui;
  font-optical-sizing: auto;
  font-style: normal;
  font-weight: bold;
  font-size: 12px;
  margin-left: -50%;
  z-index: 1000;
}

.slideOutDown {
  animation: slideOutDown 2s ease;
}

.center {
  text-align: center;
  z-index: 11;
  transform: translate(50%, -50%);
}

/* Menambah gaya tulisan italic untuk teks pada slideUpTexts */
p{
  font-size: 20px;
  font-family: "Source Code Pro", monospace;
  font-optical-sizing: auto;
  color: #06daed;
  text-shadow: 0 0 5px black,
               0 0 8px wheat,
               0 0 10px lightcyan,
               0 0 15px darkcyan;
  z-index: 1000;
}

</style>
