<template>
    <div class='cmp-banner' :style="{
      backgroundImage: `linear-gradient(to bottom, rgba(112, 112, 112, 0.25), rgba(52, 52, 52, 0.50)), url(${backgroundImagePath}  )`
    }">
      <h1 class='cmp-banner-title' :style="{ display: displayTitle }">
        Chez vous, partout et ailleurs
      </h1>
    </div>
  </template>
  
  <script >
  export default {
  data() {
    return {
        imgBg1: 'src/assets/images/eric-muhr-P_XxsdVgtpQ-unsplash.jpg',
        imgBg2: 'src/assets/images/kalen-emsley-Bkci_8qcdvQ-unsplash.jpg',
        backgroundImagePath: '',
        displayTitle: "block",
    }
  },
  mounted() {
    this.setBannerImage();
  },
  methods: {
    setBannerImage() {
      if (this.$route.path === '/') {
        this.backgroundImagePath = this.imgBg1;
      } else if (this.$route.path === '/about') {
        this.backgroundImagePath = this.imgBg2;
        this.displayTitle = 'none';
      }
    }
  }
}
  </script>
  
<style>
    .cmp-banner {
	border-radius: 20px;
	background-position: center;
	background-repeat: no-repeat;
	background-size: cover;
	height: 223px;
	display: flex;
	align-items: center;
	justify-content: center;
    
}
.cmp-banner-title {
	color: white;
	font-weight: 500;
	text-align: center;
}

</style>