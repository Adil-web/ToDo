<template>
    <b-alert v-model="showAlert" variant="success" dismissible>{{ alertMessage }}</b-alert>
</template>

<script>
export default {
    name: "Alert",
    props: ["alertMessage", "showDismissibleAlert"],
    data() {
        return {
            showAlert: false
        };
    },
    watch: {
        showAlert: {
            handler() {
                if(!this.showAlert) {
                    this.$emit("alertChanged");
                }
            }
        }
    },
    showDismissibleAlert: {
        handler() {
            this.showDismissibleAlert ? (this.showAlert = true):null;
        }
    },
};
</script>
