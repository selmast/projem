<template>
  <div>
    <h2>Signup</h2>
    <form @submit.prevent="signup">
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="password" type="password" placeholder="Password" required />
      <button type="submit">Signup</button>
    </form>
  </div>
</template>

<script>
import { auth } from "@/utils/firebase";
import { createUserWithEmailAndPassword } from "firebase/auth";

export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async signup() {
      try {
        const userCredential = await createUserWithEmailAndPassword(auth, this.email, this.password);
        console.log("User signed up:", userCredential.user);
      } catch (error) {
        console.error("Error signing up:", error);
      }
    },
  },
};
</script>
