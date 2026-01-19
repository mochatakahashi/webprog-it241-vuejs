<template>
  <section class="contact-form-section">
    <h2>Get In Touch</h2>
    <p class="contact-subtitle">Subscribe to my newsletter or send me a message!</p>
    
    <form @submit.prevent="submitForm" class="contact-form">
      <div class="form-group">
        <label for="name">Name</label>
        <input 
          type="text" 
          id="name" 
          v-model="formData.name" 
          placeholder="Your Name"
          required
        >
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input 
          type="email" 
          id="email" 
          v-model="formData.email" 
          placeholder="your.email@example.com"
          required
        >
      </div>

      <div class="form-group">
        <label for="message">Message</label>
        <textarea 
          id="message" 
          v-model="formData.message" 
          placeholder="Your message here..."
          rows="5"
          required
        ></textarea>
      </div>

      <button type="submit" class="submit-btn" :disabled="isSubmitting">
        {{ isSubmitting ? 'Sending...' : 'Send Message' }}
      </button>

      <div v-if="submitMessage" :class="['submit-message', submitStatus]">
        {{ submitMessage }}
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: 'ContactForm',
  data() {
    return {
      formData: {
        name: '',
        email: '',
        message: ''
      },
      isSubmitting: false,
      submitMessage: '',
      submitStatus: ''
    };
  },
  methods: {
    async submitForm() {
      this.isSubmitting = true;
      this.submitMessage = '';
      
      try {
        const formData = {
          access_key: '1e30e43a-0290-4e92-8a7b-532aaee37e5b',
          name: this.formData.name,
          email: this.formData.email,
          message: this.formData.message
        };
        
        const response = await fetch('https://api.web3forms.com/submit', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify(formData)
        });
        
        const result = await response.json();
        
        if (result.success) {
          this.submitMessage = 'Thank you! Your message has been received.';
          this.submitStatus = 'success';
          
          this.formData = {
            name: '',
            email: '',
            message: ''
          };
          
          setTimeout(() => {
            this.submitMessage = '';
          }, 5000);
        } else {
          this.submitMessage = result.message || 'Oops! Something went wrong. Please try again.';
          this.submitStatus = 'error';
        }
      } catch (error) {
        this.submitMessage = 'Error sending message. Please try again later.';
        this.submitStatus = 'error';
      } finally {
        this.isSubmitting = false;
      }
    }
  }
};
</script>
