<template>
  <div class="intro-wrapper">
    <button id="theme-toggle" class="theme-btn" @click="toggleTheme" aria-label="Toggle Dark Mode">
      <img v-if="!isDark" id="sun-icon" src="https://cdn-icons-png.flaticon.com/128/3917/3917817.png" alt="Sun">
      <img v-else id="moon-icon" src="https://static.vecteezy.com/system/resources/previews/017/177/956/large_2x/flat-moon-icon-on-transparent-background-free-png.png" alt="Crescent Moon">
    </button>

    <section class="hero-container">
      <div class="text-content">
        <p class="top-label">My Personal Profile</p>
        
        <h1>Hi, I'm <br> <span class="highlight-purple">Rodmina Ibe</span></h1>

        <h2 class="subtitle">IT Student at Asia Pacific College</h2>
        
        <p class="bio-text">
          Welcome to my personal portfolio! I'm glad you're here. 
          This website serves as a digital archive of my journey, featuring a 
          compilation of my life experiences, background, and the milestones 
          that define who I am today.
        </p>
      </div>

      <div class="image-content">
        <img src="/introduction/images/my-photo.png" alt="Rodmina Ibe Profile">
      </div>
    </section>

    <section class="summary-section">
      <div class="summary-container">
        <div class="section-header">
          <p class="section-subtitle">Overview</p>
          <h2>My Background Summary</h2>
        </div>

        <div class="cards-grid">
          <a href="/introduction/education.html" class="card-link">
            <div class="card">
              <div class="card-image">
                <span>
                  <img src="/introduction/images/arellano-best-in-research.jpg" alt="Education Icon" class="icon-img">
                </span>
                <div class="card-overlay">
                  <p class="click-text">Click to see more →</p>
                </div>
              </div>
              <h3>Education / Achievements</h3>
            </div>
          </a>

          <a href="/introduction/goals.html" class="card-link">
            <div class="card">
              <div class="card-image">
                <span>
                  <img src="/introduction/images/speaking-in-hackathon.jpg" alt="Goals Icon" class="icon-img">
                </span>
                <div class="card-overlay">
                  <p class="click-text">Click to see more →</p>
                </div>
              </div>
              <h3>Goals In Life / Dream</h3>
            </div>
          </a>

          <a href="/introduction/experience.html" class="card-link">
            <div class="card">
              <div class="card-image">
                <span>
                  <img src="/introduction/images/tech-external-events.jpg" alt="IT Experience Icon" class="icon-img">
                </span>
                <div class="card-overlay">
                  <p class="click-text">Click to see more →</p>
                </div>
              </div>
              <h3>IT Experience</h3>
            </div>
          </a>

          <a href="/introduction/hobbies.html" class="card-link">
            <div class="card">
              <div class="card-image">
                <span>
                  <img src="/introduction/images/gym-pic.jpg" alt="Hobbies Icon" class="icon-img">
                </span>
                <div class="card-overlay">
                  <p class="click-text">Click to see more →</p>
                </div>
              </div>
              <h3>Hobbies & Interests</h3>
            </div>
          </a>
        </div>
      </div>
    </section>

    <section class="explore-section">
      <div class="explore-container">
        <h2>Explore More</h2>
        <div class="button-group">
          <a href="/introduction/projects.html" class="explore-button">My Projects</a>
          <a href="/introduction/blogs.html" class="explore-button">My Blogs</a>
          <a href="/introduction/gallery.html" class="explore-button">Picture Gallery</a>
        </div>
      </div>
    </section>

    <ContactForm />

    <footer class="connect-section">
      <h2>Let's Connect!</h2>
      <p class="connect-text">Feel free to reach out to me on my social media platforms.</p>

      <div class="social-icons">
        <a href="https://www.linkedin.com/in/rodmina-ibe" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/128/3536/3536505.png" alt="LinkedIn">
        </a>
        <a href="https://github.com/mochatakahashi" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/128/733/733553.png" alt="GitHub"> 
        </a>
        <a href="https://www.instagram.com/rdmnjh.b_/" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/128/2111/2111463.png" alt="Instagram">
        </a>
        <a href="https://www.facebook.com/rodminajhoy.ibe.735" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/128/733/733547.png" alt="Facebook">
        </a>
        <a href="https://www.tiktok.com/@rodminajhoyibe" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/128/3046/3046121.png" alt="TikTok">
        </a>
        <a href="mailto:rodminaibe45@gmail.com">
          <img src="https://cdn-icons-png.flaticon.com/128/732/732200.png" alt="Email">
        </a>
      </div>

      <p class="copyright">© 2026 Rodmina Ibe. All Rights Reserved.</p>
    </footer>
  </div>
</template>

<script>
import ContactForm from './ContactForm.vue';

export default {
  name: 'IntroSection',
  components: {
    ContactForm
  },
  data() {
    return {
      isDark: false
    };
  },
  mounted() {
    const savedTheme = localStorage.getItem('theme');
    if (savedTheme === 'dark') {
      this.isDark = true;
      document.documentElement.setAttribute('data-theme', 'dark');
    }
  },
  methods: {
    toggleTheme() {
      this.isDark = !this.isDark;
      if (this.isDark) {
        document.documentElement.setAttribute('data-theme', 'dark');
        localStorage.setItem('theme', 'dark');
      } else {
        document.documentElement.removeAttribute('data-theme');
        localStorage.setItem('theme', 'light');
      }
    }
  }
};
</script>

<style scoped>
@import '../assets/intro-styles.css';
</style>
