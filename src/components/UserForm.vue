<template>
  <form @submit.prevent="onSubmit">
    <div class="form-group">
      <label for="username">Username: </label>
      <input
        type="text"
        name="username"
        id="username"
        class="form-control"
        v-model="username"
      />
    </div>
    <div class="form-group">
      <button class="btn btn-primary">Submit</button>
    </div>
  </form>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    const username = ref<string>();
    const onSubmit = () =>
      console.log("submited", { username: username.value });
    return { username, onSubmit };
  },
});
</script>