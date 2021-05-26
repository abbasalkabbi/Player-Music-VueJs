<template>
  <div id="control">
    <div class="circle">
      <div class="title">
        <h2>{{ title }}</h2>
      </div>
      <img src="@/assets/image/prev.png" alt="" id="prev" @click="prev()" />
      <img
        :src="imgplay"
        alt=""
        id="play"
        v-on:click="play()"
        v-if="isplaying == false"
      />
      <img
        :src="imgstop"
        alt=""
        id="play"
        v-on:click="pause()"
        v-if="isplaying == true"
      />

      <img src="@/assets/image/next.png" alt="" id="next" @click="next()" />
      <div class="footer">
        <h2>{{ namehaj }}</h2>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "ControlPlayer",
  data() {
    return {
      imgplay: require("@/assets/image/playbutton.png"),
      imgstop: require("@/assets/image/stop.png"),
    };
  },

  props: ["title", "namehaj", "isplaying"],
  methods: {
    play() {
      this.$parent.play();
    },
    pause() {
      this.$parent.pause();
    },
    next() {
      this.$parent.next();
    },
    prev() {
      this.$parent.prev();
    },
  },
};
</script>
<style>
#control {
  width: 100%;
  height: 300px;
}
.title {
  padding: 15px;
  margin: 20px auto;
  background: linear-gradient(154deg, #72147e, #ff5200);
  display: flex;
  justify-content: center;
  align-items: center;
}
.title h2 {
  color: #fff;
}
.circle {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
}
.circle img {
  width: 64px;
  height: 64px;
  margin: 10px;
  cursor: pointer;
}
.circle img:hover {
  opacity: 0.5;
}
#prev {
  transform: rotate(180deg);
}
.footer {
  width: 100%;
  height: 120px;
  background: linear-gradient(154deg, #72147e, #ff5200, #72147e, #ff5200);
  display: flex;
  justify-content: center;
  align-items: center;
}
.footer h2 {
  color: #fff;
}
</style>
