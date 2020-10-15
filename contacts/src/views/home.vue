<template>
  <div class="wrap-contacts-list">
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
          info: [
            {
              address: "1 Destiny USA Dr, Johncuse, NY 13201, United States",
              mail: "john@mail.com",
            },
          ],
        },
        {
          id: 2,
          firstName: "Mary",
          lastName: "Ann",
          phone: "975312",
          info: [
            {
              address: "2 Destiny USA Dr, Marycuse, NY 13202, United States",
              mail: "mary@mail.com",
            },
          ],
        },
        {
          id: 3,
          firstName: "Garry",
          lastName: "Neel",
          phone: "992347",
          info: [
            {
              address: "3 Destiny USA Dr, Garrycuse, NY 13203, United States",
              mail: "garry@mail.com",
            },
          ],
        },
        {
          id: 4,
          firstName: "Tom",
          lastName: "li",
          phone: "643124",
          info: [
            {
              address: "4 Destiny USA Dr, Tomcuse, NY 13204, United States",
              mail: "tom@mail.com",
            },
          ],
        },
        {
          id: 5,
          firstName: "Bobby",
          lastName: "Red",
          phone: "335721",
          info: [
            {
              address: "5 Destiny USA Dr, Bobbycuse, NY 13205, United States",
              mail: "bobby@mail.com",
            },
          ],
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
button {
  outline: none;
}

h2 {
  text-align: center;
}
</style>