<template>
  <div id="app">
    <FormWrapper v-bind:form-data="formData"/>
  </div>
</template>

<script>
import FormWrapper from "./components/FormWrapper.vue";

export default {
  name: "app",
  components: {
    FormWrapper
  },
  data: () => {
    return {
      formData: {
        text: "Prepopulated data",
        number: 23,
        date: new Date(),
        boolean: true,
        notInForm: `you ain't seen me right?`
      }
    };
  }
};
</script>

<style>
</style>
