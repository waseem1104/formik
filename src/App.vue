<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import Formik from './components/Formik.vue';
import Field from './components/Field.vue';

</script>

<template>
  <main>
    <Formik :initialValues="test" :onSubmit="handleSubmit">

      <form @submit.prevent="handleSubmit">
        <Field as="text" name="name" />
        <button>Envoyer</button>
      </form>
    </Formik>
  </main>
</template>

<style scoped>
</style>
