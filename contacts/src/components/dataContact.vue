<template>
  <li>
    <span @click="show = !show" :class="{ closeHelpInfo: show }">
      <b>{{ contact.firstName }} {{ contact.lastName }}</b>
      <span>{{ contact.phone }}</span>
      <div v-if="show && contact.info == null">
        <span><b>Please add contact additional information.</b></span>
      </div>
      <div v-if="show && contact.info != null">
        <hr />
        <span
          v-for="(item, value, index) of contact.info[0]"
          :item="item"
          :key="index"
        >
          <b>{{ value }}:</b>
          <p>{{ item }}</p>
        </span>
      </div>
    </span>

    <button class="del-contact" @click="$emit('remove-contact', contact.id)">
      &times;
    </button>

    <!-- <router-link to="/edit-info">Edit info</router-link> -->
  </li>
</template>

<script>
export default {
  props: {
    contact: {
      type: Object,
      required: true,

      info: {
        required: true,
      },
    },
  },
  data() {
    return {
      show: false,
    };
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
  transition: 0.1s ease-in-out;
}

li:hover {
  border: 1px solid rgb(175, 175, 175);
  background: rgba(204, 204, 204, 0.4);
}

/* Name contact */
li b {
  display: block;
  margin: 0 0 10px;
}

/* phone contact */
li > span > span {
  font-size: 22px;
  opacity: 0.8;
}

/* information contact */
li > span hr {
  opacity: 0.4;
}

li > span div span {
  display: block;
}

li > span div b {
  margin-top: 20px;
  opacity: 0.6;
}

li > span div p {
  opacity: 0.8;
}

li > span div {
  margin-top: 20px;
}

li > span {
  display: block;
  margin: 0 40px 0;
  cursor: pointer;
}

li > span::before {
  display: flex;
  justify-content: center;
  margin: -15px 0 5px;
  content: "click for more information";
  opacity: 0;
  transition: 0.3s ease-in-out;
}

.closeHelpInfo::before {
  content: "click for hide information";
}

li > span:hover::before {
  font-size: 14px;
  color: rgb(145, 145, 145);
  margin: 0 0 5px;
  opacity: 1;
  transition: 0.3s ease-in-out;
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
</style>