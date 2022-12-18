<template>
    <component :is="as" :name="name" :value="values.values[name]" @input="(e) => updateVal(name,e.target.value)"></component>
</template>

<script setup>
import {inject} from 'vue';

defineProps({
    name:{
        type: String,
        required:true
    },

    as: {
        type: String,
        required: true,
    },

})
const values = inject('values');
const updateVal = inject('update-val');

</script>