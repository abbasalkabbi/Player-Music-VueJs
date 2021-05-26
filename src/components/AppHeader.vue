<template>
  <div class="head">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: "AppHeader",
  props: ["title"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.head {
  width: 100%;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: cursive;
  background: linear-gradient(154deg, #72147e, #ff5200);
}
.head h1 {
  font-size: 40px;
  color: #fff;
  text-shadow: #000 12px 10px 16px;
}
</style>
