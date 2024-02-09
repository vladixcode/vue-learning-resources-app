<script setup>
import { ref, inject } from 'vue'
const titleInput = ref()
const descriptionInput = ref()
const linkInput = ref()

const formIsValid = ref(true)
const addResource = inject('addResource')
const submitData = () => {
  // Form basic validation
  if (
    titleInput.value.value.trim() === '' ||
    descriptionInput.value.value.trim() === '' ||
    linkInput.value.value.trim() === ''
  ) {
    formIsValid.value = false
    return
  }
  addResource({
    title: titleInput.value.value,
    description: descriptionInput.value.value,
    link: linkInput.value.value,
  })
}

const confirmDialog = () => (formIsValid.value = true)
</script>

<template>
  <base-dialog v-if="!formIsValid" title="Invalid input" @close="confirmDialog">
    <template #default>
      <p>Form is invalid</p>
      <p>Every input field is mandatory</p>
    </template>
    <template #actions>
      <base-button @click="confirmDialog">Ok</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" ref="titleInput" name="title" type="text" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          ref="descriptionInput"
          name="description"
          cols="30"
          rows="3"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" ref="linkInput" name="link" type="url" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

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
