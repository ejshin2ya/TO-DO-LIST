<template>
   <div class="text-right">
        <button
        type="button"
        class="btn btn-sm"
        @click="changeCurrentState('study')"
        >
        공부
        </button>
        <button
        type="button"
        class="btn btn-sm"
        @click="changeCurrentState('study')"
        >
        공부
        </button>
        <button
        type="button"
        class="btn btn-sm"
        @click="changeCurrentState('task')"
        >
        업무
        </button>
        <button
        type="button"
        class="btn btn-sm"
        @click="changeCurrentState('health')"
        >
        건강
        </button>
        <button
        type="button"
        class="btn btn-sm"
        @click="changeCurrentState('daily')"
        >
        일상
        </button>
    </div>

</template>

<script>
export default {
    
}
</script>

<style>

</style>