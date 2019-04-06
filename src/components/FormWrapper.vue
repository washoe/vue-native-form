<template>
  <div>
    <h1>My Form</h1>
    <form @submit.prevent="handleSubmit">
      <label for="text">Text</label>
      <input type="text" name="text" id="text">
      <label for="number">Number</label>
      <input type="number" name="number" id="number">
      <label for="date">Date</label>
      <input type="date" name="date" id="date">
      <label for="boolean">Boolean</label>
      <input type="checkbox" name="boolean" id="boolean">
      <button type="submit">submit</button>
    </form>
  </div>
</template>

<script>
import moment from "moment";
const formInputSetters = {
  date: (formInput, value) => {
    return (formInput.value = moment(value).format("YYYY-MM-DD"));
  },
  checkbox: (formInput, value) => (formInput.checked = value),
  default: (formInput, value) => (formInput.value = value)
};

const populateForm = (formElement, formData) => {
  Object.entries(formData).forEach(entry => {
    const formInput = formElement[entry[0]];
    if (formInput) {
      const value = entry[1];
      (formInputSetters[formInput.type] || formInputSetters.default)(
        formInput,
        value
      );
    }
  });
};

export default {
  name: "FormWrapper",
  props: {
    formData: Object
  },
  mounted: function() {
    populateForm(this.$el.querySelector("form"), this.formData);
  },
  methods: {
    handleSubmit: function(event) {
      const formObject = [...new FormData(event.target)].reduce(
        (result, item) => {
          return { [item[0]]: item[1], ...result };
        },
        {}
      );
      console.log("form submit", formObject);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
