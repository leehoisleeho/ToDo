<template>
  <div>
    <div class="container">
      <div class="todoBox" v-for="(item, index) in MianTodoList" :key="item.id">
        <div class="todo" :id="index">
          <div class="todoInfo">{{ item.todoInfi }}</div>
          <div class="slh">
            <img
              src="../../public/btn_1.png"
              alt=""
              @touchstart="done(item.id, index)"
            />
          </div>
        </div>
        <div class="btn" @touchstart="wc(index, item.id)">完成</div>
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
      MianTodoList: this.TodoList,
      wjl: true,
      listId: null,
    };
  },
  watch: {
    MianTodoList() {
      if (this.MianTodoList === "") {
        this.wjl = true;
      } else {
        this.wjl = false;
      }
    },
  },
  methods: {
    wc(index, id) {
      let TodoListArr = this.TodoList;
      for (let index = 0; index < TodoListArr.length; index++) {
        if (id === TodoListArr[index].id) {
          TodoListArr.splice(index, 1);
        }
      }
    },
    done(id, index) {
      this.listId = id;
      let dom = document.getElementById(index);
      let arr = dom.classList;
      let doms = document.querySelectorAll(".todo");
      if (arr.length === 1) {
        for (let i = 0; i < doms.length; i++) {
          doms[i].classList.remove("todoActive");
        }
        arr.add("todoActive");
      } else if (arr.length === 2) {
        arr.remove("todoActive");
      }
    },
  },
};
</script>

<style>
.todoBox {
  width: 90vw;
  margin-top: 0.2rem;
  border-radius: 0.2rem;
  overflow: hidden;
  position: relative;
}
.btn {
  width: 1.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #34a853;
  position: absolute;
  height: 1rem;
  right: 0.01rem;
  z-index: 1;
  bottom: 0;
  font-size: 0.3rem;
  color: white;
}
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
  transition: all 0.65s;
  z-index: 2;
  position: relative;
}
.todoActive {
  transform: translateX(-1.5rem);
}

.todo > div:nth-child(1) {
  width: 70%;
  font-size: 0.28rem;
  padding-left: 0.3rem;
}
.todo > div:nth-child(2) {
  width: 30%;
  justify-content: flex-end;
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
.slh {
}
.slh > img {
  width: 0.5rem;
}
</style>
