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
          <select class="col-2" v-model="category">
            <option disabled value="">카테고리</option>
            <option value="study">공부</option>
            <option value="work">업무</option>
            <option value="daily">일상</option>
            <option value="health">건강</option>
          </select>

          <input
            type="text"
            class="col-8"
            placeholder="해야할 일을 입력해주세요"
            ref="userInput"
            @keyup.enter="addTodo"
            v-model="newTodoItem"
          />
          <button class="col-2" @click="addTodo">추가</button>
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
      newTodoItem: "",
      todoList: [],
      category: "",
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
    addTodo() {
      //inputbox가 빈값인지 체크, 아니면 로직 수행
      if (this.newTodoItem !== "") {
        //로컬스토리지에 해당 카테고리값이 널값이 아니면 기존에 저장된 리스트 불러오기
        if (localStorage.getItem(this.category) != null) {
          this.todoList = JSON.parse(localStorage.getItem(this.category));
        }
        //todoList에 새 할일 넣어주기
        this.todoList.push({
          label: this.newTodoItem,
        });
        //다시 JSON형태로 변환해서 local에 넣어주기
        this.todoList = JSON.stringify(this.todoList);
        localStorage.setItem(this.category, this.todoList);
        //입력창, 옵션 선택 초기화
        this.newTodoItem = "";
        this.category = "";
        this.$refs.userInput.focus();
      }
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
