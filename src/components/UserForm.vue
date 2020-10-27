<template>
  <form @submit.prevent="onSubmit">
    <div class="form-group">
      <label for="username">Username: </label>
      <validation-provider rules="required" v-slot="{ errors }">
        <input
          type="text"
          name="username"
          id="username"
          class="form-control"
          v-model="username"
        />
        <span>{{ errors[0] }}</span>
      </validation-provider>
    </div>
    <div class="form-group">
      <button class="btn btn-primary">Submit</button>
    </div>
  </form>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { extend, ValidationProvider } from "vee-validate";
import { required } from "vee-validate/dist/rules";

extend("required", {...required, message: "ohhh" });

export default defineComponent({
  components: { ValidationProvider },
  setup() {
    const username = ref<string>();
    const onSubmit = () =>
      console.log("submited", { username: username.value });
    return { username, onSubmit };
  },
});
</script>