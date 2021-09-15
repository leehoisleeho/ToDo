<template>
  <div class="footer" v-show="zz">
    <input
      type="text"
      name=""
      placeholder="添加待办事项"
      v-focus
      v-model="inputInfo"
    />
    <button class="btn_1" @click="add" v-btn>保存</button>
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  name: "MyFoorer",
  data() {
    return {
      inputInfo: "",
    };
  },
  props: ["zz", "addList"],
  watch: {
    zz() {
      if (this.zz === false) {
        this.inputInfo = "";
      }
    },
  },
  methods: {
    add() {
      const todoObj = {
        id: nanoid(),
        todoInfi: this.inputInfo,
      };
      this.addList(todoObj, false);
    },
  },
  directives: {
    focus: {
      update(e) {
        e.focus();
      },
    },
    btn: {
      update(x, y, z) {
        let inputInfo = z.context.inputInfo;
        if (inputInfo === "") {
          z.elm.style.color = "#999";
        } else {
          z.elm.style.color = "#0e73ff";
        }
      },
    },
  },
};
</script>

<style scoped>
.footer {
  position: absolute;
  bottom: 0;
  height: 1.95rem;
  width: 100vw;
  background: white;
  border-top-right-radius: 0.4rem;
  border-top-left-radius: 0.4rem;
  display: flex;
  justify-content: center;
}
.footer > input {
  width: 90vw;
  margin: 0 auto;
  height: 0.6rem;
  outline: none;
  border: none;
  margin-top: 0.3rem;
  font-size: 0.3rem;
}
.btn_1 {
  padding: 0.2rem 0.2rem;
  position: absolute;
  bottom: 0.2rem;
  right: 0.25rem;
  border: none;
  background: white;
  color: #999;
  font-size: 0.3rem;
}
</style>>
