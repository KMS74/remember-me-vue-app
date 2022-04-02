<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>Unfortunately, at least one input value is invalid</p>
      <p>
        Please check all inputs and make sure you enter at least a few
        characters in each input filed
      </p>
    </template>
    <template #actions>
      <base-button type="button" v-on:click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <!-- TODO use third part library for example 'VeeValidate' to validate input felid -->
    <form v-on:submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" name="description" rows="3" ref="desInput" />
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>
      <base-button type="submit">Add Resource</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      let enteredTitle = this.$refs.titleInput.value;
      let enteredDescription = this.$refs.desInput.value;
      let enteredLink = this.$refs.linkInput.value;
      //validate inputs
      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredLink.trim() === ''
      ) {
        // inputs are invalid
        this.inputIsInvalid = true;
        return; //  *IMPORTANT stops the execution of the method
      }

      this.addResource(enteredTitle, enteredDescription, enteredLink);
      // TODO clears all inputs data after adding a resource
      this.clearInputs();
    },
    clearInputs() {
      this.$refs.titleInput.value = '';
      this.$refs.desInput.value = '';
      this.$refs.linkInput.value = '';
    },
    confirmError() {
      this.inputIsInvalid = false;
    },
  },
  inject: ['addResource'],
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
