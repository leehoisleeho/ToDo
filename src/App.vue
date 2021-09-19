<template>
  <div id="app">
    <div class="zz" v-if="zz" @click="xiaoshi"></div>
    <MyHeader />
    <MyMain :TodoList="TodoList" />
    <MyFooter :zz="zz" :TodoList="TodoList" :addList="addList" />
    <div class="logoBtn" @click="showInfo">
      <img src="../public/add.png" alt="" />
    </div>
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
      TodoList: [],
    };
  },
  methods: {
    showInfo() {
      this.zz = !this.zz;
    },
    xiaoshi() {
      this.zz = !this.zz;
    },
    addList(e, bool) {
      this.TodoList.unshift(e);
      this.zz = bool;
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
  background: #f5f5f5;
}
.zz {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgb(83, 83, 83);
}
.logoBtn {
  width: 1rem;
  height: 1rem;
  position: fixed;
  bottom: 0.2rem;
  left: 50%;
  transform: translateX(-0.5rem);
  z-index: -1;
}
.logoBtn > img {
  width: 100%;
  vertical-align: middle;
}
</style>
