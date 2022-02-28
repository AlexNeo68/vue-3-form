<template>
  <form @submit.prevent="onSubmit">
    <BaseInput
      label="Email"
      type="email"
      v-model="email"
      :error="errors.email"
    />

    <BaseInput
      label="Password"
      v-model="password"
      :error="errors.password"
      type="password"
    />

    <BaseButton type="submit" class="-fill-gradient"> Submit </BaseButton>
  </form>
</template>

<script>
import { useField, useForm } from "vee-validate";
import { object, string, number } from "yup";
export default {
  setup() {
    const validationSchema = object({
      email: string().required().email(),
      password: string().required("A strong password is required").min(6),
    });

    const { handleSubmit, errors } = useForm({
      validationSchema,
      initialValues: {},
    });

    const { value: email } = useField("email");
    const { value: password } = useField("password");

    const onSubmit = handleSubmit((values) => {
      console.log("submit", values);
    });

    return {
      onSubmit,
      email,
      password,
      errors,
    };
  },
};
</script>
