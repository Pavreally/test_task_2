<template>
  <li class="contact-item">
    <b>{{ contact.firstName }} {{ contact.lastName }}</b>
    <span> {{ contact.phone }} </span>
    <button class="del-contact" @click="$emit('remove-contact', contact.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    contact: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
li {
  border: 1px solid #ccc;
  margin: 0 0 10px;
  padding: 15px 5px;
  position: relative;
  width: 100%;
  max-width: 500px;
  min-width: 250px;
}

.del-contact {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 24px;
  border: none;
  cursor: pointer;
  opacity: 0.5;
}

.del-contact:hover {
  opacity: 1;
}

.contact-item b {
  display: block;
  margin: 0 0 10px;
}

.contact-item span {
  font-style: italic;
}
</style>