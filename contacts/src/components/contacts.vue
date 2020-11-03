<template>
  <div>
    <ul>
      <dataContact
        v-for="(dataContact, index) of reverseContacts"
        :dataContact="dataContact"
        :key="index"
        @remove-contact="removeContact"
      />
    </ul>
  </div>
</template>

<script>
import dataContact from "@/components/dataContact";

export default {
  props: ["listContacts"],
  components: {
    dataContact,
  },
  methods: {
    removeContact(id) {
      if (confirm("Delete this contact? Are you sure?")) {
        this.$emit("remove-contact", id);
      }
    },
  },
  computed: {
    // get reverse object array
    reverseContacts(dataContact, id) {
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