<template>
  <div>
    <span>{{ item.title }}</span>
    

    <button @click="handleCompleted">완료</button>
    <button @click="handleDeleted">제거</button>
  </div>
</template>

<script setup lang="ts">
import { PropType, computed, ref } from 'vue';
import { Todo } from '@/api/model/todo';

const props = defineProps({
    item: {
        type: Object as PropType<Todo>,
        default: null,
    }
})

const emit = defineEmits(['completed', 'deleted']);

const name = ref('한승훈');

const convertedName = computed(() => {
    props.item
    return name.value + '123';
})

function handleCompleted() {
    emit('completed');
}

function handleDeleted() {
    emit('deleted');
}
</script>