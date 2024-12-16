<script setup>
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';
import { useStore } from '../store';
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const firstName = ref("");
const lastName = ref("");
const email = ref("");
const username = ref("");
const password = ref("");
const confPassword = ref("");
const store = useStore();
const router = useRouter();

const handleRegister = () => {
  event.preventDefault();

  if (!firstName.value) {
    alert('First Name is required.');
  } else if (!lastName.value) {
    alert('Last Name is required.');
  } else if (!email.value) {
    alert('Email is required.');
  } else if (!password.value) {
    alert('Password is required.');
  } else if (!confPassword.value) {
    alert('Re-entering the password is required.');
  } else if (password.value !== confPassword.value) {
    alert('Passwords do not match.');
  } else {
    store.email = email.value
    store.password = password.value
    store.firstName = firstName.value
    store.lastName = lastName.value
    store.password = password.value
    router.push("/movies");
  }
};
</script>

<template>
  <Header />
  <div class = "hero">
    <form class="login" @submit.prevent="handleRegister">
      <input required v-model="firstName" placeholder = "First Name">
      <input required v-model="lastName" placeholder = "Last Name">
      <input required v-model="username" placeholder = "Username">
      <input type="email" required v-model="email" placeholder = "E-mail">
      <input type="password" required v-model="password" placeholder = "Password">
      <input type="password" required v-model="confPassword" placeholder = "Confirm your password">
      <button type="register">Sign-up</button>
    </form>
  </div>
  <Footer />
</template>

<style scoped>
.hero {
  display:flex;
  align-items: center;
  justify-content: center;
  padding: 80px;
}
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #000;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

form.login {
  
  background-color: #fff;
  padding: 30px 20px;
  border-radius: 8px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  width: 90%;
  max-width: 400px;
  text-align: center;
}

form.login input {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 2px solid #ff0000;
  border-radius: 4px;
  outline: none;
  font-size: 1rem;
}

form.login input:focus {
  border-color: darkred;
  box-shadow: 0 0 5px rgba(255, 0, 0, 0.5);
}

form.login button[type="register"] {
  width: 100%;
  padding: 10px;
  background-color: #ff0000;
  color: #fff;
  text-transform: uppercase;
  font-weight: bold;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

form.login button[type="register"]:hover {
  background-color: darkred;
}
</style>
