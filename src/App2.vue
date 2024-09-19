<script>
export default {
  data() {
    return {
      name: "John Doe",
      status: "active",
      tasks: ["Task one", "Task two", "Task three"],
      link: "https://www.google.com/search?q=google&oq=google&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIYCAEQLhhDGIMBGMcBGLEDGNEDGIAEGIoFMgYIAhBFGDsyDAgDECMYJxiABBiKBTIGCAQQRRg8MgYIBRBFGDwyBggGEEUYPDIGCAcQBRhA0gEIMTc1NmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8",
    };
  },

  methods: {
    toggleStatus() {
      if (this.status === "active") {
        this.status = "pending";
      } else if (this.status === "pending") {
        this.status = "inactive";
      } else {
        this.status = "active";
      }
    },
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">Status is active</p>
  <p v-else-if="status === 'pending'">Status is pending</p>
  <p v-else>User is inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">{{ task }}</li>
  </ul>

  <a :href="link">Go to google</a> <br />

  <button @click="toggleStatus">Toggle status</button>
</template>
