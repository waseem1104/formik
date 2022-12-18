<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import Formik from './components/Formik.vue';
import Field from './components/Field.vue';

const initialValues = {
  email: 'jewa@gmail.com',
};

const onSubmit = (values) => {
    alert(JSON.stringify(values, null, 2));
}

const validate = (values) => {
  const errors = {}

  if (!values.email) {
    errors.email = 'Required'
  } else if (!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,}$/i.test(values.email)) {
    errors.email = 'Invalid email address'
  }

  return errors
}

</script>

<template>
  <main>
    <Formik v-slot="{handleSubmit}" :initialValues="initialValues" :onSubmit="onSubmit" :validate="validate">
      <form @submit.prevent="handleSubmit">
        <div>
          <Field as="input" name="email" />
        </div>
        <button type="submit">Envoyer</button>
      </form>
    </Formik>
  </main>
</template>

<style scoped>
</style>
