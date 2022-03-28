<template>
    <div class="todo__list-item" :class="{'todo__list-item--done': completed}">
        <div  
            class="todo__list-item-check" 
            :class="{'todo__list-item-check--done': completed}"
            @click="toggleCompleted(index)"
        >
        </div>
        <p class="list-item__text">
            {{ text }}
        </p>
        <div 
            class="todo__list-item-remove" 
            :class="{'todo__list-item-remove--done': completed}"
            @click="removeTask(index)"
        >
        </div>
    </div>
</template>

<script>
export default {
    props: {
        completed: Boolean,
        text: String,
        index: Number,
    },
    methods: {
        removeTask(index) {
            if (confirm('Вы точно приняли решение о удалении задачи? В последствии это может координально изменить вашу жизнь!')) {
                this.$emit('onRemoveTask', index);
            }
        },
        toggleCompleted(index) {
            this.$emit("onToggleCompleted", index);
        }
    }
}
</script>