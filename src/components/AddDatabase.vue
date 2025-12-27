<script setup>
import { ref } from "vue";

const form = ref({
  name: "",
  dbname: "databases",
  host: "db",
  port: 5432,
  username: "restorely",
  password: "restorely",
});

const error = ref(null);

async function submitForm() {
  error.value = null;

  const res = await fetch("http://localhost:8080/databases", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify(form.value),
  });

  console.log(res);

  if (!res.ok) {
    error.value = await res.text();
    return;
  }

  form.value = {
    name: "",
    dbname: "databases",
    host: "db",
    port: 5432,
    username: "restorely",
    password: "restorely",
  };
}
</script>

<template>
  <div class="max-w-xl mx-auto p6">
    <h2 class="text-2xl font-bold mb-6">Add Database</h2>

    <form @submit.prevent="submitForm" class="space-y-4">
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="form.name" required />

      <label for="dbname">Database name:</label>
      <input type="text" id="dbname" v-model="form.dbname" required />

      <label for="host">Host:</label>
      <input type="text" id="host" v-model="form.host" required />

      <label for="port">Port:</label>
      <input type="number" id="port" v-model.number="form.port" required />

      <label for="username">Username:</label>
      <input type="text" id="username" v-model="form.username" required />

      <label for="password">Password:</label>
      <input type="password" id="password" v-model="form.password" required />

      <button type="submit" class="btn w-full">Add Database</button>
    </form>

    <p v-if="error" class="text-red-400 mt-4">{{ error }}</p>
  </div>
</template>
