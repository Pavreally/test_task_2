<template>
  <li>
    <h4>{{ contact.firstName }}</h4>
    <span>
      {{ contact.phone }}
    </span>
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
  padding: 10px 5px;
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
}
</style>