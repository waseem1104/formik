<template>
        <slot :values="values" :handleSubmit="handleSubmit"></slot>
</template>

<script setup>
import {reactive} from 'vue';


const values = reactive({
    values: props.initialValues
});

const errors = ref({})
const isSubmitting = ref(false)

const handleSubmit = () => {
    props.onSubmit(values.values);
}

const props = defineProps({
    onSubmit:{
        type: Function,
        required:true
    },
    initialValues: {
        type: Object,
        required:true
    },
    validate : {
        type: Function,
        required:true
    }
});


provide('values', values);
</script>

<style scoped></style>