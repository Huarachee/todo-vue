<template>
    <div class="todo__add-field">
        <input 
            class="add-field__input"
            @keyup.13="addTask" 
            v-model="text" type="text" 
            placeholder="Напишите напоминалку..."
        >
        <button 
            class="add-field__btn" 
            @click="addTask"
        >
            <img src="../assets/images/add-icon.svg" alt="add icon" width="25" height="25">
        </button>
    </div>
</template>

<script>
export default {
    data: () => ({
       text: "", 
    }),
    methods: {
        addTask() {
            if (this.text) {
                this.$emit('onAddTask', this.text);
                this.text = "";
            }
        }
    }
}
</script>