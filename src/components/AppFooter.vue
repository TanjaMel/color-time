<template>
  <v-footer class="footer-section" padless>
    <v-container>
      <v-row class="py-8" align="start" justify="space-between">
        <!-- Logo + Slogan -->
        <v-col cols="12" md="3" class="mb-6 mb-md-0">
          <img src="@/assets/logo_white.png" alt="Logo" height="70" class="mb-2" />
          <p class="footer-slogan">When time makes sense.</p>
        </v-col>

        <!-- Navigation -->
        <v-col cols="6" md="3">
          <h4 class="footer-title">Navigation</h4>
          <ul class="footer-links">
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#contact-us">Contact</a></li>
          </ul>
        </v-col>

        <!-- Contact -->
        <v-col cols="6" md="3">
          <h4 class="footer-title">Contact</h4>
          <p class="footer-text">hello@tempus.com</p>
          <p class="footer-text">+123 456 7890</p>
          <div class="social-icons mt-2">
            <v-icon small class="mr-2">mdi-facebook</v-icon>
            <v-icon small class="mr-2">mdi-instagram</v-icon>
            <v-icon small>mdi-twitter</v-icon>
          </div>
        </v-col>
      </v-row>

      <v-divider class="my-4" />

      <!-- Copyright -->
      <v-row justify="center">
        <p class="footer-bottom">© {{ new Date().getFullYear() }} Tempus. All rights reserved.</p>
      </v-row>
    </v-container>
  </v-footer>
</template>

<style scoped>
.footer-section {
  background-color: #0f172a; /* dark blue/black */
  color: #ffffff;
  padding-top: 48px;
  padding-bottom: 24px;
  font-family: 'Red Hat Display', sans-serif;
}

.footer-title {
  font-size: 16px;
  font-weight: 600;
  margin-bottom: 8px;
  color: #ffffff;
}

.footer-slogan {
  font-size: 24px;
  color: #ffffff;
}

.footer-text {
  font-size: 14px;
  color: #cbd5e1;
  margin-bottom: 4px;
}

.footer-links {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links a {
  color: #cbd5e1;
  text-decoration: none;
  font-size: 14px;
  display: inline-block;
  margin-bottom: 6px;
  transition: color 0.3s;
}

.footer-links a:hover {
  color: #3b82f6;
}

.social-icons v-icon {
  color: #cbd5e1;
  cursor: pointer;
  transition: color 0.3s;
}

.social-icons v-icon:hover {
  color: #3b82f6;
}

.footer-bottom {
  font-size: 13px;
  color: #64748b;
}
</style>
