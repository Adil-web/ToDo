<template>
    <table class="table table-dark table-stripped table-hover">
        <thead class="thead-light">
            <tr>
                <th>№</th>
                <th>Мои задачи</th>
                <th>Выполнено?</th>
                <th>Изменить</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(task, index) in toDoList" :key="task.id">
                <td>{{ index+1 }}</td>
                <td>{{ task.title }}</td>
                <td v-if="task.is_completed">Выполнено</td>
                <td v-else>Не выполнено</td>
                <td><Buttons :task='task' @updating='emitUpdateUp' @deleting='emitDeleteUp'/></td>
            </tr>
        </tbody>
    </table>
</template>

<script>
import Buttons from './Buttons.vue'
export default {
    name: 'TableTasks',
    props: ['toDoList'],
    methods: {
        emitUpdateUp(task) {
            this.$emit('updateRequest', task)
        },
        emitDeleteUp(task) {
            this.$emit('deleting', task)
        }
    },
    components: {
        Buttons,
    },
}
</script>
