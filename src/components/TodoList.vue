<template>
  <div class="text-right">
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

<style></style>
