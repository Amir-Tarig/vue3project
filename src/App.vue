<template>
  <h1>{{ title }}</h1>

  <teleport to="#modals" v-if="showModal">
    <Modal @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Using a Slot</h1>
      <p>This is how i pass a some custom template in to my componenet</p>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>sign up to the newsletter</h1>
      <p>For updates and promo codes</p>
    </Modal>
  </teleport>
  <br>
  <button @click.alt="toggleModal">Show Modal(alt)</button>
  <button @click="toggleModalTwo">Open Modal</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title : 'My First Vue 3 Project',
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
#app ,#modals{
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
  padding-bottom:10px ;
}
</style>
