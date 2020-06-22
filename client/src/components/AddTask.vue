<template>
    <input type="button" value="Добавить задачу" class="btn btn-primary" @click="$emit('newTask')">
</template>

<script>
export default {
    name: 'AddTask',
}
</script>
