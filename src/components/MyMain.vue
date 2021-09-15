<template>
  <div>
    <div class="container">
      <div
        class="todo"
        @click="touch(item.id, $event)"
        v-for="(item, index) in MianTodoList"
        :key="index"
      >
        <div class="todoInfo">{{ item.todoInfi }}</div>
        <div v-if="done">
          <button>完成</button>
          <button>删除</button>
        </div>
      </div>
      <div class="wjl" v-if="wjl">
        <img src="../../public/wjl.png" alt="" />
        <p>暂时没有待办事项</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyMain",
  props: ["TodoList"],
  data() {
    return {
      done: false,
      MianTodoList: this.TodoList,
      wjl: true,
    };
  },
  watch: {
    MianTodoList() {
      if (this.MianTodoList === "") {
        return;
      } else {
        this.wjl = false;
      }
    },
  },
  methods: {
    touch(id, e) {
      console.log(e.target);
    },
  },
};
</script>

<style  scoped>
.container {
  display: flex;
  align-items: center;
  padding: 0.2rem 0;
  flex-direction: column;
}
.todo > div {
  display: flex;

  align-items: center;
}
.todo {
  display: flex;
  width: 90vw;
  height: 1rem;
  background: white;
  border-radius: 0.2rem;
  margin: 0.2rem;
}

.todo > div:nth-child(1) {
  width: 70%;
  font-size: 0.28rem;
  padding: 0.3rem;
}
.todo > div:nth-child(2) {
  width: 30%;
  justify-content: space-evenly;
}
.todo > div:nth-child(2) > button {
  border: none;
  border-radius: 0.1rem;
  padding: 0.08rem 0.2rem;
  color: white;
}
.todo > div:nth-child(2) > button:nth-child(1) {
  background: #34a853;
}
.todo > div:nth-child(2) > button:nth-child(2) {
  background: #ea4335;
}
.wjl {
  width: 4rem;
  height: 3rem;
  margin-top: 0.5rem;
}
.wjl > img {
  width: 100%;
}
.wjl > p {
  text-align: center;
  color: #999;
}
</style>
