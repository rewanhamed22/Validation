<template>
  <form
    @click.prevent="onSubmit"
    class="bg-white shadow-md rounded-lg w-1/2 mx-auto my-5 p-8"
  >
    <div class="mb-6">
      <label for="email">Email</label>
      <Input id="email" type="email" placeholder="Enter your email" />
    </div>

    <Button
      class="w-full btn bg-emerald-300 hover:bg-primary-700 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-white transition-colors duration-300 ease-in-out"
    >
      Click me
    </Button>
  </form>
</template>

<script setup lang="ts">
import { useForm } from "vee-validate";
import * as v from "valibot";
import { toTypedSchema } from "@vee-validate/valibot";

const { values, handleSubmit } = useForm({
  validationSchema: toTypedSchema(
    v.object({
      name: v.pipe(v.string()),
      email: v.pipe(v.string(), v.nonEmpty("required"), ),
      password: v.pipe(
        v.string(),
        v.minLength(6, "Must be at least 6 characters")
      ),
    })
  ),
});

const onSubmit = handleSubmit((submitted) => {
  submitted.email.endsWith("@gmail.com");
  console.log(submitted.email);
});
</script>
