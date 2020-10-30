<template>
  <div class="wrap-contacts-list">
    <addContact @add-contact="addContact" />
    <contacts :listContacts="listContacts" @remove-contact="removeContact" />
  </div>
</template>

<script>
import axios from "axios";
import addContact from "@/components/addContact";
import contacts from "@/components/contacts";

const dataUrl = "http://localhost:3000/listContacts";

export default {
  name: "App",
  components: {
    contacts,
    addContact,
  },
  data() {
    return {
      listContacts: [],
    };
  },
  mounted() {
    this.getContacts();
  },
  methods: {
    getContacts() {
      axios
        .get(dataUrl)
        .then((response) => (this.listContacts = response.data));
    },
    addContact(dataContact) {
      axios
        .post(dataUrl, dataContact)
        .then((response) => this.listContacts.push(dataContact));
      console.log("(Check #2) New ID added: " + dataContact.id);
    },
    removeContact(id) {
      // the problem with sending id (before updating page)
      axios
        .delete(`${dataUrl}/${id}`)
        .then(
          (this.listContacts = this.listContacts.filter((t) => t.id !== id))
        );

      console.log(`Deleted ID: ${id}`);
    },
  },
  computed: {
    getLastId() {
      let lastId = this.listContacts.length;
    },
  },
};
</script>

<style>
button {
  outline: none;
}
</style>