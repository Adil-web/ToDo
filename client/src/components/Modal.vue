<template>
    <div>
        <b-from class="w-100">
            <b-form-group id="form-description-group">
                <div>
                    <b-form-input
                        type="text"
                        required
                        :state="validation"
                        placeholder="Ваша задача"
                        v-model="tempTitle">
                    </b-form-input>
                </div>
            </b-form-group>
        </b-from>
    </div>
</template>

<script>
export default {
    name: "Modal",
    props: ["task", "updateOrAdd"],
    data() {
        return {
            tempTitle: "",
            checked: []
        };
    },
    computed: {
        validation() {
            return this.tempTitle.length > 3 && this.tempTitle.length < 30;
        }
    },
    created() {
        if(this.updateOrAdd) {
            this.tempTitle = this.task.title;
            this.task.is_completed ? (this.checked = ["true"]) : (this.checked = [])
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault();
            let form = {};
            if(this.tempTitle.length < 4 || this.tempTitle.length > 30) return;
            form.title = this.tempTitle;
            this.checked[0] == "true" ? (form.is_completed = true):(form.is_completed = false);
            form.id = this.task.id;
            this.updateOrAdd ? this.$emit("updating", form):this.$emit("addNew", form);
        },
        onReset(e) {
            e.preventDefault();
            if(this.updateOrAdd) {
                this.tempTitle = this.task.title;
                this.task.is_completed ? (this.checked = ["true"]) : this.checked.pop();
            }else{
                this.tempTitle = "";
                this.checked.pop();
            }
        }
    }
}
</script>
