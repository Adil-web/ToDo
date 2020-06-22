<template>
    <div>
        <button type="button"
                class="btn btn-secondary btn-sm"
                @click="updateTask(t)">
            Обновить
        </button>
        &nbsp;
        <button type="button"
                class="btn btn-danger btn-sm"
                @click="deleteTask(t)">
            X
        </button>
    </div>
</template>

<script>
export default {
    name: 'Buttons',
    props: ['task'],
    methods: {
        updateTask(task) {
            this.$emit('updating', task)
        },
        deleteTask(task) {
            this.$emit('deleting', task)
        },
    }
}
</script>