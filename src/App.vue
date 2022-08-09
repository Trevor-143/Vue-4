<template>
  <h1>{{title}}</h1>
  <!-- <input type="text" ref="name">
  <button @click="handleClick">Just Click</button> -->

  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal" >
      <template v-slot:links>
        <a href="#">Sign Up</a>
        <a href="#">More Info</a>
      </template>
      <h1>Hey How are you doing</h1>
      <p>Well... Am doing ok, i guess</p>
    </Modal>
  </teleport>
  

  <teleport to=".modals" v-if="showModalTwo">
    <Modal theme="sale" @leave="toggleModalTwo">
    
      <h1>Hey, What Are You Doing</h1>
      <p>I am Coding with Vue JS</p>
    </Modal>
  </teleport>

  <button @click.alt="toggleModal">Sign Up Today (alt)</button>
  <button @click.shift="toggleModalTwo">Log In (shift)</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My first Vue Apps',
      header: 'Sign up Today!',
      text: 'Just do it Now',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
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
  color: #ffffff;
  background: #000000; 
  border-radius: 7px;
  text-align: center;
  padding: 20px 25px;
}
input {
  background: #ffd5d5;
  border: none;
  padding: 15px;
  margin: 15px;
  border-radius: 7px;
}
button {
  padding: 10px;
  margin: 7px;
  border: none;
  background: #000000;
  color: #ffffff;
  border-radius: 7px;
  cursor: pointer;
}
</style>
