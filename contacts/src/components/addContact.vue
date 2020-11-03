<template>
  <form @submit.prevent="onSubmit">
    <div
      class="add-contact btn"
      :class="{ rotate45: !showForm }"
      @click="showForm = !showForm"
    ></div>
    <span :class="{ hidden: showForm }">
      <span>First Name:</span>
      <input type="text" v-model="inputFirstName" />
      <span>Last Name:</span>
      <input type="text" v-model="inputLastName" />
      <span>Phone Number: </span>
      <input type="text" v-model="inputPhoneNumber" />
      <button class="btn" type="submit">Create Contact</button>
    </span>
  </form>
</template>

<script>
export default {
  // get variable from home.vue
  props: ["lastId"],
  data() {
    return {
      inputFirstName: "",
      inputLastName: "",
      inputPhoneNumber: "",
      showForm: true,
    };
  },
  methods: {
    // event send to json new contact
    onSubmit() {
      if (
        this.inputFirstName.trim() &&
        this.inputLastName.trim() &&
        this.inputPhoneNumber.trim()
      ) {
        const newContact = {
          id: this.lastId + 1,
          firstName: this.inputFirstName,
          lastName: this.inputLastName,
          phone: this.inputPhoneNumber,
        };

        // send new item object
        this.$emit("add-contact", newContact);
        // clear UI elements form
        this.inputFirstName = "";
        this.inputLastName = "";
        this.inputPhoneNumber = "";
      }
    },
  },
};
</script>

<style scoped>
.hidden {
  height: 0;
  opacity: 0;
}

.rotate45 {
  background: rgb(236, 182, 175);
  transform: rotate(45deg);
}

form {
  display: flex;
  align-items: center;
  flex-direction: column;
}

form span {
  overflow: hidden;
  margin: 24px 0 0;
  opacity: 1;
  transition: 0.5s ease-in-out;
}

form span span {
  font-weight: bold;
  font-size: 14px;
  float: left;
  clear: left;
  margin: 0 0 5px;
}

form span input {
  max-width: 250px;
  min-width: 250px;
  border: #ccc 1px solid;
  font-size: 18px;
  float: left;
  clear: left;
  outline: none;
  margin: 0 0 20px;
  padding: 5px 5px;
  width: 100%;
}

form div {
  background: rgb(199, 199, 199);
  transform: rotate(0deg);
  transition: 0.1s ease-in-out;
}

.btn {
  color: #fff;
  border: none;
  cursor: pointer;
}

form span button {
  background: rgb(103, 173, 238);
  font-size: 20px;
  font-weight: bold;
  float: left;
  clear: left;
  padding: 5px 10px;
  margin: 10px 0 30px 50%;
  transform: translateX(-50%);
  width: 250px;
}

form span button:hover {
  background: rgb(127, 184, 236);
}

.add-contact {
  border-radius: 100%;
  font-size: 38px;
  font-weight: bold;
  height: 44px;
  display: flex;
  align-items: center;
  flex-direction: column;
  margin: 15px 0 0;
  width: 44px;
}

.add-contact:hover {
  opacity: 0.8;
}

.add-contact::before {
  content: "+";
}
</style>