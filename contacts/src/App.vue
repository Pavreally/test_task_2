<template>
  <div id="app" class="wrap-contacts-list">
    <h2>Contacts</h2>
    <addContact @add-contact="addContact" :lastId="lastContactId" />
    <contacts :listContacts="listContacts" @remove-contact="removeContact" />
  </div>
</template>

<script>
import contacts from "@/components/contacts";
import addContact from "@/components/addContact";

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
        },
        {
          id: 2,
          firstName: "Mary",
          lastName: "Geel",
          phone: "975312",
        },
        {
          id: 3,
          firstName: "Garry",
          lastName: "Neel",
          phone: "992347",
        },
        {
          id: 4,
          firstName: "Timmy",
          lastName: "li",
          phone: "643124",
        },
        {
          id: 5,
          firstName: "Bobby",
          lastName: "Red",
          phone: "335721",
        },
      ],
    };
  },
  components: {
    contacts,
    addContact,
  },
  methods: {
    removeContact(id) {
      this.listContacts = this.listContacts.filter((t) => t.id !== id);
    },
    addContact(contact) {
      this.listContacts.push(contact);
    },
    lastContactId() {
      return this.listContacts[this.listContacts.length - 1].id;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

button {
  outline: none;
}

h2 {
  text-align: center;
}
</style>
