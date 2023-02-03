<template>
  <base-dialog v-if="dataIsInvalid" title="Invalid input" @close="confirmError">
    <template #default>
      <p>Unfortunatly, at leeast one input is Invalid.</p>
      <p>
        Please make shure you enter at least a few charecters into each field.
      </p>
    </template>
    <template #actions>
      <base-button @click="confirmError">OK</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" v-model="enteredTitle" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          v-model="enteredDescription"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">link</label>
        <input id="link" name="link" type="url" v-model="enteredLink" />
      </div>
      <div>
        <base-button type="submit">Add resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from "../UI/BaseButton.vue";
export default {
  components: { BaseButton },
  emits: ["add-resource"],
  inject: ["addResource"],
  data() {
    return {
      dataIsInvalid: false,
      enteredTitle: "",
      enteredDescription: "",
      enteredLink: "",
    };
  },
  methods: {
    submitData() {
      if (
        this.enteredTitle.trim() === "" ||
        this.enteredDescription.trim() === "" ||
        this.enteredLink.trim() === ""
      ) {
        this.dataIsInvalid = true;
        return;
      }
      this.addResource(
        this.enteredTitle,
        this.enteredDescription,
        this.enteredLink
      );
    },
    confirmError() {
      this.dataIsInvalid = false;
    },
  },
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
