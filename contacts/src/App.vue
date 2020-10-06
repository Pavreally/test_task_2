<template>
  <div id="app">
    <contacts :listContacts="listContacts" @remove-contact="removeContact" />
  </div>
</template>

<script>
import contacts from "@/components/contacts";

export default {
  name: "App",
  data() {
    return {
      listContacts: [
        {
          id: 1,
          firstName: "John",
          lastName: "York",
          phone: "687234",
          mail: "john@mail.com",
        },
        {
          id: 2,
          firstName: "Mary",
          lastName: "Geel",
          phone: "975312",
          mail: "mary@mail.com",
        },
        {
          id: 3,
          firstName: "Garry",
          lastName: "Neel",
          phone: "992347",
          mail: "garry@mail.com",
        },
        {
          id: 4,
          firstName: "Timmy",
          lastName: "li",
          phone: "643124",
          mail: "timmy@mail.com",
        },
        {
          id: 5,
          firstName: "Bobby",
          lastName: "Red",
          phone: "335721",
          mail: "bobby@mail.com",
        },
      ],
    };
  },
  components: {
    contacts,
  },
  methods: {
    removeContact(id) {
      this.listContacts = this.listContacts.filter((t) => t.id !== id);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
</style>
