<script>
export default {
  props: {
    picture: {
      type: Array,
      required: true,
    },
  },

  data() {
    return {
      count: 0,
    };
  },

  methods: {
    handleIncrement() {
      this.count = this.count + 1 >= this.picture.length ? 0 : this.count + 1;
    },
    handleDecrement() {
      this.count = this.count - 1 < 0 ? this.picture.length - 1 : this.count - 1;
    },
  },
};
</script>
<template>

    <div :style="{ backgroundImage: `url(${picture[count]})` }" class="cmp-carousel">
      <div>
        <div class="cmp-btn-carousel">
          <i class="fa-solid fa-chevron-left" @click="handleDecrement"></i>
          <i class="fa-solid fa-chevron-right" @click="handleIncrement"></i>
        </div>
        <p>{{ count + 1 }} / {{ picture.length }}</p>
      </div>
    </div>

</template>
<style>
    .cmp-carousel {
	width: 100%;
	height: 415px;
	border-radius: 25px;
	display: flex;
	align-items: center;
	/* flex-direction: column; */
	background-position: center;
	background-repeat: no-repeat;
	background-size: cover;
	position: relative;
}
.cmp-carousel > div {
	width: 100%;
	display: flex;
	flex-direction: column;
	align-items: center;
}
.cmp-carousel > div > p {
	color: white;
	position: absolute;
	bottom: 0;
	left: 50;
}
.cmp-carousel > div > .cmp-btn-carousel {
	display: flex;
	width: 100%;
	justify-content: space-between;
}
.cmp-carousel > div > .cmp-btn-carousel > i {
	color: white;
	font-size: 50px;
	padding: 0 10px 0;
}
.cmp-carousel > div > .cmp-btn-carousel > i:hover {
	color: #ff6060;
	cursor: pointer;
}

</style>