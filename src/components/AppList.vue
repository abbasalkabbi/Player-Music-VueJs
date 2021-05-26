<template>
  <div class="list">
    <ul>
      <li v-for="m in music" :key="m.id" @click="list(m.id)">
        {{ m.title }},{{ m.artist }}
      </li>
    </ul>
  </div></template
>
<script>
export default {
  name: "AppList",
  data() {
    return {};
  },
  props: ["music", "index"],
  methods: {
    list(id) {
      this.$parent.list(id);
    },
  },
};
</script>

<style scoped>
.list {
  width: 100%;
  height: 100%;
}
.list ul {
  list-style: none;
  width: 100%;
  height: 100%;
}

.list ul li {
  margin: auto;
  width: 90%;
  height: 40px;
  background: oldlace;
  margin-top: 10px;
}
</style>
