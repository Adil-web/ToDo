<template>
    <div>
        <h3>Задач в списке {{ total }}, из них выполнено {{  doneTasks }}.</h3>
    </div>
</template>

<script>
export default {
    name: "NumberOfTasks",
    props: ["toDoList"],
    computed: {
        total() {
            return this.toDoList.length;
        },
        doneTasks() {
            let d = 0;
            for(let task of this.toDoList){
                if(task.is_completed == true) d++;
            }
            return d;
        }
    }
};
</script>
