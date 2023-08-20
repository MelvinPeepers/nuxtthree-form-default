<template>
  <div class="container">
  
          <h1>Netlify Forms on Nuxt 3</h1>
  
          <h2>Contact Form</h2>
  
          <p>Have any questions or suggestions?</p>
  
          <form 
              name="contact" 
              method="POST" 
              data-netlify="true"
              action="thank you"
          >
  
              <input type="hidden" name="form-name" value="contact" />
  
              <div class="row">
  
                  <div class="column">
                      <label>Name</label>
                      <input type="text" name="name" placeholder="Full name here">
                  </div>
  
                  <div class="column">
                      <label for="email">Email</label>
                      <input type="email" name="email" placeholder="Email">
                  </div>
  
              </div>
  
              <div class="row">
  
                  <div class="column">
                      <label>Title</label>
                      <input type="text" name="title" placeholder="Title of message">
                  </div>
  
              </div>
  
              <div class="row">
                  <div class="column">
                      <label>Message</label>
                      <textarea name="message" placeholder="Leave your message here"></textarea>
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
    message: '',
  });
  
  const handleSubmit = async () => {
    const formDataToSend = new FormData();
  
    for (const key in formData) {
      formDataToSend.append(key, formData[key]);
    }
  
    try {
      const response = await fetch('/', {
        method: 'POST',
        body: formDataToSend,
      });
  
      if (response.ok) {
        alert('Form submitted successfully!');
        // Handle success actions or redirects here
      } else {
        console.error('Error submitting the form');
        // Handle error cases here
      }
    } catch (error) {
      console.error('Error submitting the form:', error);
      // Handle error cases here
    }
  };
  </script>

