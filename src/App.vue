<template>
  <h1>{{ title }}</h1>
  <img alt="Vue logo" src="./assets/logo.png" />
  <teleport to=".modals" v-if="showModal">
    <Modal @close="toggleModal">
      <h1>Hello Fundboxers!</h1>
      <p>Grab your vue cool goodies!</p>
      <template #links>
        <a href="#">sign up</a>
        <a href="#">login</a>
      </template>
    </Modal>
  </teleport>
  <template v-if="showModal2">
    <Modal @close="toggleModal2">
      <h1>Form</h1>
      <input type="text" />
    </Modal>
  </template>
  <button @click.alt="toggleModal">Open Modal1 (alt)</button>
  <button @click="toggleModal2">Open modal2</button>
</template>

<script>
import Modal from "@/components/Modal.vue";
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "Vue is cool!",
      showModal: false,
      showModal2: false,
      // modalState: "closed",
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
    // setNewModal(newType) {
    //   console.log({ newType, modal: this.modalState });
    //   this.modalState = newType === this.modalState ? "closed" : newType;
    // },
  },
};
</script>

<style>
#app,
.modal {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
