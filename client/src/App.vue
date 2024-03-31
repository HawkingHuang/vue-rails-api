<template>
  <div id="contacts">
    <div v-for="(contact, index) in contacts" :key="contact.id">
      <p>{{ contact.name }} is my {{ contact.relationship }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contacts: [],
    };
  },
  methods: {
    async fetchContacts() {
      const res = await fetch("http://localhost:3000/contacts");
      const data = await res.json();
      console.log(data);
      this.contacts = data;
    },
  },
  mounted() {
    this.fetchContacts();
  },
};
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
