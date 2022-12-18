<template>
    <component :is="as"></component>
</template>

<script setup>

defineProps({
    name:{
        type: String,
        required:true
    },
    type: {
        type: String,
        required:true
    },

    as: {
        type: String,
        required: true,
        default: 'input'
    },

    placeholder: {
        type: String,
        default:''
    },

})

const values = inject('values');
</script>