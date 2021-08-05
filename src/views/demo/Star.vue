<template>
  <div class="content">
    <div class="stars">
      <div
        class="star"
        v-for="(item, index) in starNum"
        :key="index"
        ref="star"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "",
  components: {},
  props: {},
  data() {
    return {
      starNum: 800, //星星数量
      distance: 800, //间距
    };
  },
  created() {},
  // 生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {
    let starArr = this.$refs.star;
    starArr.forEach((item) => {
      let speed = 0.1 + Math.random() * 1;
      let thisDistance = this.distance + Math.random() * 300;
      item.style.transformOrigin = `0 0 ${thisDistance}px`;
      item.style.transform = `
      translate3d(0,0,-${thisDistance}px) 
      rotateY(${Math.random() * 360}deg) 
      rotateX(${Math.random() * -50}deg) 
      scale(${speed},${speed})
      `;
    });
  },
};
</script>

<style scoped>
/* 定义动画 */
@keyframes myrotate {
  0% {
    transform: perspective(400px) rotateZ(20deg) rotateX(-40deg) rotateY(0);
  }
  100% {
    transform: perspective(400px) rotateZ(20deg) rotateX(-40deg)
      rotateY(-360deg);
  }
}

.content {
  /* background: radial-gradient(200% 100% at bottom center, #f7f7b6, #e96f92, #1b2947); */
  background: radial-gradient(
    220% 105% at top center,
    #1b2947 10%,
    #75517d 40%,
    #e96f92 65%,
    #f7f7b6
  );
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
}
.stars {
  transform: perspective(500px);
  transform-style: preserve-3d;
  position: absolute;
  left: 50%;
  bottom: 0;
  perspective-origin: 50% 100%;
  animation: myrotate 90s infinite linear;
}

.star {
  width: 2px;
  height: 2px;
  background: #f7f7b8;
  position: absolute;
  top: 0;
  left: 0;
  backface-visibility: hidden;
}
</style>
