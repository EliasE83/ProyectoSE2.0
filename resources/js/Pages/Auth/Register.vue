<script setup>
import { Head, Link, useForm } from '@inertiajs/vue3';
import AuthenticationCard from '@/Components/AuthenticationCard.vue';
import AuthenticationCardLogo from '@/Components/AuthenticationCardLogo.vue';
import Checkbox from '@/Components/Checkbox.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
  <Head title="Register" />

  <section class="bg-white">
    <div class="lg:grid lg:min-h-screen lg:grid-cols-12">
      
      <aside
            class="relative block h-16 lg:order-last lg:col-span-5 lg:h-full xl:col-span-6"
          >
            <img
              alt="Pattern"
              src="https://mx.arauco.com/medias/Arauco-Negro1.jpg-515Wx515H?context=bWFzdGVyfGltYWdlc3wxMDA0MDl8aW1hZ2UvanBlZ3xoZDAvaGUxLzkwNTE4MTkwNDg5OTAvQXJhdWNvX05lZ3JvMS5qcGdfNTE1V3g1MTVIfDI1OWZlZTU1NGZmZjJjNmQ1OTkyMjZiYjk1MzRiNzVjYTQ0YzI1NWZhZjI3NTJmNDMyZDVjOGU5M2M4MjdhNDE"
              class="absolute inset-0 h-full w-full object-cover"
            />

        <div class="hidden lg:relative lg:block lg:p-12">
          <a class="block text-blue-200" href="/">
            <img src="images/UPQLOGOREDONDO.png" alt="" width="60" height="60">
                <span class="sr-only">Home</span>
                
              </a>

          <h2 class="mt-6 text-2xl font-bold text-white sm:text-3xl md:text-4xl">
            Servicios Estudiantiles 🐦
          </h2>

          <p class="mt-4 leading-relaxed text-white/90">
            Lorem, ipsum dolor sit amet consectetur adipisicing elit. Eligendi nam
            dolorum aliquam, quibusdam aperiam voluptatum.
          </p>
        </div>
      </aside>

      <main
        aria-label="Main"
        class="flex items-center justify-center px-8 py-8 sm:px-12 lg:col-span-7 lg:py-12 lg:px-16 xl:col-span-6"
      >
        <div class="max-w-xl lg:max-w-3xl">
          
        <form @submit.prevent="submit">
            <div>
                <InputLabel for="name" value="Name" />
                <TextInput
                    id="name"
                    v-model="form.name"
                    type="text"
                    class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
                    required
                    autofocus
                    autocomplete="name"
                />
                <InputError class="mt-2" :message="form.errors.name" />
            </div>

            <div class="col-span-6">
              <InputLabel for="email" value="Email" />
                <TextInput
                    id="email"
                    v-model="form.email"
                    type="email"
                    name="email"
                    class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
                    required
                />
                <InputError class="mt-2" :message="form.errors.email" />
            </div>

            <div class="col-span-6 sm:col-span-3">
              <InputLabel for="password" value="Password" />
                <TextInput
                    id="password"
                    v-model="form.password"
                    type="password"
                    name="password"
                    class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
                    required
                    autocomplete="new-password"
                />
                <InputError class="mt-2" :message="form.errors.password" />
            </div>

            <div class="col-span-6 sm:col-span-3">
              <InputLabel for="password_confirmation" value="Confirm Password" />
                <TextInput
                    id="password_confirmation"
                    v-model="form.password_confirmation"
                    type="password"
                    name="password_confirmation"
                    class="mt-1 w-full rounded-md border-gray-200 bg-white text-sm text-gray-700 shadow-sm"
                    required
                    autocomplete="new-password"
                />
                <InputError class="mt-2" :message="form.errors.password_confirmation" />
            </div>

            <div class="col-span-6 sm:flex sm:items-center sm:gap-4">
              <button
                class="inline-block shrink-0 rounded-md border border-blue-600 bg-blue-600 px-12 py-3 text-sm font-medium text-white transition hover:bg-transparent hover:text-blue-600 focus:outline-none focus:ring active:text-blue-500"
              >
                Crear cuenta
              </button>

              <p class="mt-4 text-sm text-gray-500 sm:mt-0">
                Already have an account?
                <a href="/login" class="text-gray-700 underline">Log in</a>.
              </p>
            </div>
          </form>
        </div>
      </main>
    </div>
  </section>

</template>
