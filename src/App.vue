<template>
  <h1>{{title}}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
  <div v-if="showModal">
    <Modal :header="header" :text="text" :theme="sale" @close="toggleModal" />
  </div>
  <br>
  <button @click="toggleModal">Show Modal</button>

</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App', 
  data() {
    return {
      title: 'My first Vue app',
      header: 'Sign up',
      text: 'You are awesome!!!',
      showModal: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value)
      this.title = this.$refs.name.value
    },
    toggleModal() {
      this.showModal = !this.showModal
    }
  },
  components: {
    Modal,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
