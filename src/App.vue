<!-- /src/App.vue -->

<template>
    <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput></TodoInput>
      <TodoList></TodoList>
      <TodoFooter></TodoFooter>
    </div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoList from './components/TodoList';
import TodoInput from './components/TodoInput';
import TodoFooter from './components/TodoFooter';

export default {
    components: {
      'TodoHeader': TodoHeader,
      'TodoInput': TodoInput,
      'TodoList': TodoList,
      'TodoFooter': TodoFooter
    }
}
</script>

<style>

</style>