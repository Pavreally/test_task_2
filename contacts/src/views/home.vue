<template>
  <div class="wrap-contacts-list">
    <addContact @add-contact="addContact" :lastId="getLastId" />
    <contacts :listContacts="listContacts" @remove-contact="removeContact" />
  </div>
</template>

<script>
import axios from "axios";
import addContact from "@/components/addContact";
import contacts from "@/components/contacts";

// db (json-server)
const dataUrl = "http://localhost:3000/listContacts";

export default {
  name: "App",
  components: {
    contacts,
    addContact,
  },
  data() {
    return {
      listContacts: [{}],
    };
  },
  mounted() {
    // render object list from db json
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
    },
    removeContact(id) {
      axios
        .delete(`${dataUrl}/${id}`)
        .then(
          (this.listContacts = this.listContacts.filter((t) => t.id !== id))
        );
    },
  },
  computed: {
    // get last item id of the object array
    getLastId(lastId) {
      lastId = this.listContacts.slice(-1)[0].id;
      return lastId;
    },
  },
};
</script>

<style>
button {
  outline: none;
}
</style>