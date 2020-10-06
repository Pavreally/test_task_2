<template>
  <div>
    <h2>Contacts</h2>
    <button class="add-contact">
      <span>&times;</span>
    </button>
    <ul>
      <contact
        v-for="contact of listContacts"
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
      if (confirm("Удалить этот контакт?")) {
        this.$emit("remove-contact", id);
      }
    },
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
}

ul {
  list-style: none;
  padding: 0;
  justify-content: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin: 0 10px 0;
}

.add-contact {
  background: rgb(103, 173, 238);
  color: #fff;
  border: none;
  font-size: 40px;
  font-weight: bold;
  border-radius: 100%;
  cursor: pointer;
  margin: 0 50% 20px;
  padding: 0 11px;
  transform: translateX(-50%) rotate(45deg);
}
</style>