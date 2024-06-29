<template>
  <form
    @click.prevent="onSubmit"
    class="bg-white shadow-md rounded-lg w-1/2 mx-auto my-5 p-8"
  >
    <div class="mb-6">
      <Input
        type="email"
        class="w-full px-3 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-primary-600 focus:border-primary-600 dark:bg-gray-800 dark:border-gray-600 dark:text-[#12b488] dark:focus:ring-green-500 dark:focus:border-green-500"
        placeholder="name@company.com"
        required
      />
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
import { object, string } from "zod";
import { toTypedSchema } from "@vee-validate/zod";
const { values, handleSubmit } = useForm({
  validationSchema: toTypedSchema(
    object({
      email: string().min(1, "required"),
    })
  ),
});
const onSubmit =handleSubmit((submitted) => {
  submitted.email.endsWith("@gmail.com");
});
</script>
