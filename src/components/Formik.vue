<template>
        <slot :isSubmitting="isSubmitting" :values="values" :errors="errors" :handleSubmit="handleSubmit"></slot>
</template>

<script setup>
import {reactive, ref, provide} from 'vue';

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

const values = reactive({
    values: props.initialValues
});

const errors = ref({})
const isSubmitting = ref(false)

const handleSubmit = () => {

    console.log('HANDLE SUBMIT');
    const err = props.validate(values.values);

    if(Object.keys(err).length == 0) {
        props.onSubmit(values.values);
    }else{
        errors.value = err;
        console.error(errors.value);
    }
    
}

const updateVal = (name,value) => {
    console.log('UPDATE');
    values.values[name] = value
}


provide('values', values);
provide('update-val',updateVal)
</script>

<style scoped></style>