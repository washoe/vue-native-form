<template>
  <div id="app">
    <FormWrapper v-bind:form-data="formData"/>
  </div>
</template>

<script>
import FormWrapper from './components/FormWrapper.vue'

export default {
  name: 'app',
  components: {
    FormWrapper
  },
  data: () => {
    return {
      formData: {text: 'Prepopulated data', notInForm: 23}
    }
  }
}
</script>

<style>
</style>
