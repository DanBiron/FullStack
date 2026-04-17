<template>
    <div class="grid h-screen lg:grid-cols-2">
    <div class="flex items-center justify-center px-5">
      <div class="w-full max-w-96">
        <h1 class="text-2xl font-bold tracking-tight lg:text-3xl">Welcome back</h1>
        <p class="mt-1 text-muted-foreground">Log in to your account to continue.</p>

        <form class="mt-8" @submit="submit">
          <fieldset :disabled="isSubmitting" class="grid gap-5">
            <UiVeeInput label="Email" type="email" name="email" placeholder="john@example.com" autocomplete="email" />
            <UiVeeInput label="Password" type="password" name="password" autocomplete="current-password" />
            <div class="flex items-center justify-between">
              <UiVeeCheckbox label="Remember me" name="remember" />
              <NuxtLink
                class="text-sm font-medium text-primary underline-offset-2 hover:underline"
                to="#"
                >Forgot password?</NuxtLink
              >
            </div>
            <UiButton  class="w-full" type="submit" text="Log in" />
          </fieldset>
        </form>

        <UiDivider class="my-6" label="OR" />

        <div class="grid gap-3">
          <UiButton variant="outline" type="button" @click="signInWithGoogle()">
            <Icon class="size-4" name="logos:google-icon" />
            <span class="ml-2">Continue with Google</span>
          </UiButton>
        </div>

        <p class="mt-6 text-sm text-muted-foreground">
          Don't have an account?
          <NuxtLink to="/sign-up" class="font-semibold text-primary underline-offset-2 hover:underline" 
            >Create account</NuxtLink
          >
        </p>
      </div>    
    </div>
    <div class="hidden bg-muted lg:block">
      <div class="flex h-full flex-col items-center justify-center p-8">
        <img src="/FE_logo1_white-removebg-preview.png" alt="Logo">
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { boolean, object, string } from "yup";
import type { InferType } from "yup";

definePageMeta({
  layout: false
})

  const supabase = useSupabaseClient();
  
  useSeoMeta({
    title: "Welcome back - Log in",
    description: "Log in to your account to continue.",
  });

  const LoginSchema = object({
    email: string().email().required().label("Email"),
    password: string().required().label("Password").min(8),
    remember: boolean().label("Remember me"),
  });

  const { handleSubmit, isSubmitting } = useForm<InferType<typeof LoginSchema>>({
    validationSchema: LoginSchema,
  });

  const submit = handleSubmit(async (values) => {
    const { error } = await supabase.auth.signInWithPassword({
      email: values.email,
      password: values.password,
    });

    if (error) {
      useSonner("Login failed", {
        description: error.message,
      });
      return;
    }

    useSonner("Logged in successfully!", {
      description: "You have successfully logged in.",
    });

    await navigateTo("/admin/super-admin");
  });

  const signInWithGoogle = () => {
    useSonner("Continue with Google", {
      description: "Redirecting to Google...",
    });
  };
</script>