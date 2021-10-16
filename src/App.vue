<template>
  <h1>{{title}}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
  <teleport to=".modals" v-if="showModal">
    <Modal :theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Hi</h1>
      <p>Hello friends!!!</p>
    </Modal>
  </teleport>

  <br>
  <button @click.alt="toggleModal">Show Modal (alt)</button>

  <br>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">      
      <h1>Another modal window</h1>
      <p>You are awesome!!!</p>
    </Modal>
  </teleport>
  <br>
  <button @click="toggleModalTwo">Show Modal Two</button>


  

</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App', 
  data() {
    return {
      title: 'My first Vue app',      
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value)
      this.title = this.$refs.name.value
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    },
  },
  components: {
    Modal,
  }
}
</script>

<style>
#app, .modals {
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
