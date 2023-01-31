<template>
    <button  @click="onClick()" :style="{background: color}" class="btn" >{{ showAddTask ? 'Close' : 'Add Task'}}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        showAddTask: {type: Boolean},
        color: {type:String}
    },
    methods: {
        onClick() {
            this.$emit('btn-click');
        }
    }
}
</script>