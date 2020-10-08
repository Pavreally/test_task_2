<template>
  <div>
    <ul>
      <contact
        v-for="contact of sortContacts"
        :contact="contact"
        :key="contact.id"
        @remove-contact="removeContact"
      />
    </ul>
  </div>
</template>

<script>
import contact from "@/components/dataContacts";

export default {
  props: ["listContacts"],
  components: {
    contact,
  },
  methods: {
    removeContact(id) {
      if (confirm("Delete this contact? Are you sure?")) {
        this.$emit("remove-contact", id);
      }
    },
  },
  computed: {
    sortContacts(contact, id) {
      return this.listContacts.slice().reverse();
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin: 0 10px 0;
}
</style>