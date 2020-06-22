<template>
    <div>
        <h1>{{ task.title }}</h1>
        <h2 v-if='updateOrAdd'>True</h2>
        <h2 v-else>False</h2>
        <b-form @submit="onSubmit" @reset="onReset" class="w-100">
        <b-form-group id="form-description-group">
            <b-form-input id="form-description-input" type="text" required placeholder="Your task" v-model='task.title'>
            </b-form-input>
        </b-form-group>
        <b-form-group id="form-complete-group">
            <b-form-checkbox-group id="form-checks" v-model='task.is_completed'>
            <b-form-checkbox  value="true">Задача выполнена?</b-form-checkbox>
            </b-form-checkbox-group>
        </b-form-group>
            <b-button type="submit" variant="primary">Подтвердить</b-button>
            <b-button type="reset" variant="danger">Сброс</b-button>
        </b-form>
    </div>
</template>
<script>
export default {
    name: 'Modal',
    props: ['task', 'updateOrAdd'],
    data(){
        return{
            form: {
                title: '',
                checked: []
            },
        }
    },
    methods:{
        onSubmit(e){
            e.preventDefault();
            // console.log(this.form.checked)
            // this.form.checked[0] ? this.task.is_completed = [true] : this.task.is_completed = [false];
            // console.log('То, что отправляем в task' + this.task.is_completed);
            this.$emit('adding', this.task)
        },
        onReset(e){
            e.preventDefault();
            this.task.title = '',
            this.task.is_completed = false

        }
    }
}
</script>