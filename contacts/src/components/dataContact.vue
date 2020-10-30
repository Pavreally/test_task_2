<template>
  <li>
    <span @click="showInfo = !showInfo" :class="{ closeHelpInfo: showInfo }">
      <b>{{ dataContact.firstName }} {{ dataContact.lastName }}</b>
      <span>{{ dataContact.phone }}</span>
      <div v-if="showInfo && dataContact.info == null">
        <router-link class="btn-edit" tag="div" to="/edit-contact" />
        <span><b>Please add additional information.</b></span>
      </div>
      <div v-if="showInfo && dataContact.info != null">
        <hr />
        <router-link class="btn-edit" tag="div" to="/edit-contact" />
        <span
          v-for="(item, value, index) of dataContact.info[0]"
          :item="item"
          :key="index"
        >
          <b>{{ value }}:</b>
          <p>{{ item }}</p>
        </span>
      </div>
    </span>

    <button class="remove-contact" @click="$emit('remove-contact', dataContact.id)">
      &times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    dataContact: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      showInfo: false,
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

/* Button delete contact */
.remove-contact {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 24px;
  border: none;
  cursor: pointer;
  opacity: 0.5;
}

.remove-contact:hover {
  opacity: 1;
}

/* Button link to edit contact */
.btn-edit {
  background: #c7c7c7;
  border-radius: 100%;
  margin: 20px 0 0 50%;
  font-size: 24px;
  font-weight: bold;
  color: #ffffff;
  height: 30px;
  cursor: pointer;
  width: 30px;
  transform: translateX(-50%);
}

.btn-edit:hover {
  opacity: 0.8;
}

.btn-edit::after {
  content: "+";
}
</style>