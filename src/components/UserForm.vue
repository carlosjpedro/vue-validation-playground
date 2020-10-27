<template>
  <Form v-slot="{ errors }">
    <div class="form-group">
      <label for="username">Username: </label>

      <Field
        as="input"
        type="text"
        name="username"
        id="username"
        class="form-control"
        v-model="username"
        :rules="isRequired"
      />
      <span>{{ errors.username }}</span>
    </div>
    <div class="form-group">
      <button class="btn btn-primary">Submit</button>
    </div>
  </Form>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { Form, Field } from "vee-validate";

export default defineComponent({
  components: { Form, Field },
  setup() {
    const username = ref<string>();

    const isRequired = (value: unknown) => (value ? true : false);

    const onSubmit = () =>
      console.log("submited", { username: username.value });
    return { username, onSubmit, isRequired };
  },
});
</script>