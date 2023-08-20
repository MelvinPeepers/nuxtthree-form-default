<template>
  <div class="container">
    <h1>Netlify Forms on Nuxt 3</h1>
    <h2>Contact Form</h2>
    <p>Have any questions or suggestions?</p>
    <form 
      name="contact" 
      method="POST" 
      data-netlify="true"
      action="#"
      @submit.prevent="handleSubmit"
    >
      <input type="hidden" name="form-name" value="contact" />
      <div class="row">
        <div class="column">
          <label>Name</label>
          <input type="text" name="name" v-model="formData.name" placeholder="Full name here">
        </div>
        <div class="column">
          <label for="email">Email</label>
          <input type="email" name="email" v-model="formData.email" placeholder="Email">
        </div>
      </div>
      <div class="row">
        <div class="column">
          <label>Title</label>
          <input type="text" name="title" v-model="formData.title" placeholder="Title of message">
        </div>
      </div>
      <div class="row">
        <div class="column">
          <label>Message</label>
          <textarea name="message" v-model="formData.message" placeholder="Leave your message here"></textarea>
        </div>
      </div>
      <div class="vertical-center">
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<style>
@import url("~/assets/styling.css");
</style>

<script setup>
import { ref } from 'vue';

const formData = ref({
  name: '',
  email: '',
  title: '', // Add this line for the title field
  message: '',
});

const handleSubmit = async () => {
  // No need for manual form submission handling
  // The nuxtForms module will handle form submissions and Netlify integration
};
</script>


