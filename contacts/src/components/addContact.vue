<template>
  <form class="add-contact-wrap" @submit.prevent="onSubmit">
    <div
      class="add-contact btn-add"
      :class="{ rotate45: rotateButton }"
      @click="(showForm = !showForm), (rotateButton = !rotateButton)"
    ></div>
    <span :class="{ hidden: showForm }">
      <span>First Name:</span>
      <input type="text" v-model="inputFirstName" />
      <span>Last Name:</span>
      <input type="text" v-model="inputLastName" />
      <span>Phone Number: </span>
      <input type="text" v-model="inputPhoneNumber" />
      <button class="btn-add" type="submit">Create contact</button>
    </span>
  </form>
</template>

<script>
export default {
  props: {
    lastId: {
      type: Function,
    },
  },
  data() {
    return {
      inputFirstName: "",
      inputLastName: "",
      inputPhoneNumber: "",
      showForm: true,
      rotateButton: false,
    };
  },
  mounted() {
    this.lastId();
  },
  methods: {
    onSubmit() {
      if (
        this.inputFirstName.trim() ||
        this.inputLastName.trim() ||
        this.inputPhoneNumber.trim()
      ) {
        let newContact = {
          id: this.lastId() + 1,
          firstName: this.inputFirstName,
          lastName: this.inputLastName,
          phone: this.inputPhoneNumber,
        };

        this.$emit("add-contact", newContact);
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
}

.rotate45 {
  opacity: 0.5;
  transform: rotate(45deg);
}

.add-contact-wrap {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.add-contact-wrap span {
  overflow: hidden;
  margin: 24px 0 20px;
  transition: 0.1s ease-in-out;
}

.add-contact-wrap span span {
  float: left;
  clear: left;
  margin: 0 0 20px;
  width: 120px;
}

.add-contact-wrap span input {
  float: left;
  border: #ccc 1px solid;
  font-size: 18px;
  outline: none;
}

.add-contact-wrap span button {
  float: left;
  clear: left;
}

.btn-add {
  background: rgb(103, 173, 238);
  color: #fff;
  border: none;
  cursor: pointer;
}

.add-contact-wrap span button {
  font-size: 20px;
  padding: 5px 10px;
  margin: 10px 0 0 50%;
  transform: translateX(-50%);
}

.add-contact {
  border-radius: 100%;
  font-size: 38px;
  font-weight: bold;
  height: 44px;
  display: flex;
  align-items: center;
  flex-direction: column;
  width: 44px;
}

.add-contact::before {
  content: "+";
}
</style>