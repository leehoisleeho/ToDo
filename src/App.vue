<template>
  <div id="app">
    <div class="zz" v-if="zz" @click="xiaoshi"></div>
    <MyHeader />
    <MyMain />
    <MyFooter />
    <div class="logoBtn" @click="showInfo"></div>
  </div>
</template>

<script>
import MyFooter from "./components/MyFooter.vue";
import MyHeader from "./components/MyHeader.vue";
import MyMain from "./components/MyMain.vue";
export default {
  name: "App",
  components: { MyHeader, MyFooter, MyMain },
  data() {
    return {
      zz: false,
    };
  },
  methods: {
    showInfo() {
      this.zz = !this.zz;
    },
    xiaoshi() {
      this.zz = !this.zz;
    },
  },
};
</script>

<style>
/* 公共样式 */
* {
  margin: 0;
  padding: 0;
  list-style: none;
  box-sizing: border-box;
}

html {
  font-size: calc(100vw / 7.5);
}

body {
  font-size: 0.18rem;
}
.zz {
  position: absolute;
  z-index: -1;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgb(83, 83, 83);
}
.logoBtn {
  width: 1rem;
  height: 1rem;
  border: 1px solid red;
  position: fixed;
  bottom: 0;
}
</style>
