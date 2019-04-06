<template>
  <div>
    <h1>My Form</h1>
    <form @submit.prevent="handleSubmit">
      <label for="text">Text</label>
      <input type="text" name="text"/>
      <button type="submit">submit</button>
    </form>
  </div>
</template>

<script>

export default {
  name: "FormWrapper",
  props: {
    formData: Object
  },
  methods: {
    handleSubmit: function (event) {
      console.log('form submit', event.target);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
