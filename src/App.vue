<template>
  <div id="app">
    <div class="container">
      <div class="col-md-6 offset-md-3">
        <h1 class="text-center mb-4">Todo 어플리케이션</h1>

        <div class="row justify-content-evenly">
          <button
            type="button"
            :class="[
              currentType === 'all'
                ? 'col-2 btn btn-secondary'
                : 'col-2 btn btn-outline-secondary',
            ]"
            @click="changeCurrentType('all')"
          >
            전체
          </button>
          <button
            type="button"
            :class="[
              currentType === '공부'
                ? 'col-2 btn btn-secondary'
                : 'col-2 btn btn-outline-secondary',
            ]"
            @click="changeCurrentType('공부')"
          >
            공부
          </button>
          <button
            type="button"
            :class="[
              currentType === '업무'
                ? 'col-2 btn btn-secondary'
                : 'col-2 btn btn-outline-secondary',
            ]"
            @click="changeCurrentType('업무')"
          >
            업무
          </button>
          <button
            type="button"
            :class="[
              currentType === '건강'
                ? 'col-2 btn btn-secondary'
                : 'col-2 btn btn-outline-secondary',
            ]"
            @click="changeCurrentType('건강')"
          >
            건강
          </button>
          <button
            type="button"
            :class="[
              currentType === '일상'
                ? 'col-2 btn btn-secondary'
                : 'col-2 btn btn-outline-secondary',
            ]"
            @click="changeCurrentType('일상')"
          >
            일상
          </button>
        </div>

        <div class="list-group mb-4">
          <button
            class="list-group-item text-left"
            v-for="todo in activeTodoList"
            :key="todo"
            @click="toggleTodoState(todo)"
          >
            {{ todo.label }}
          </button>
        </div>

        <div class="row justify-content-evenly">
          <select class="col-2" v-model="selected">
            <option disabled value="">주제선택</option>
            <option>공부</option>
            <option>업무</option>
            <option>건강</option>
            <option>일상</option>
          </select>

          <input
            class="col-8"
            type="text"
            v-model="userInput"
            placeholder="해야할 일을 입력해주세요"
            ref="userInput"
            @keyup.enter="addNewTodo"
          />

          <button class="col-2" @click="addNewTodo">입력</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      userInput: "",
      selected: "",
      todoList: [],
      currentType: "all",
    };
  },
  computed: {
    activeTodoList() {
      return this.todoList.filter(
        (todo) => this.currentType === "all" || todo.type === this.currentType
      );
    },
  },
  methods: {
    // changeCurrentState(state) {
    //   this.currentState = state;
    // },
    changeCurrentType(type) {
      this.currentType = type;
    },
    addNewTodo() {
      this.todoList.push({
        type: this.selected,
        label: this.userInput,
        state: "active",
      });
      this.userInput = "";
      this.$refs.userInput.focus();
    },
    toggleTodoState(todo) {
      todo.state = todo.state === "active" ? "done" : "active";
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
