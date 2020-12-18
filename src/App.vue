<template>
  <h1> {{ title }} </h1> 
  <p>Welcome ...</p>
  <!-- <Modal header="Sign up for the Giveaway" text="Grab your ninja sawg for half price!"/> -->
  <!-- <Modal :header="['shaun', 4]" text="Grab your ninja sawg for half price!"/> -->
  <div v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal"/> -->

    <!-- default slots-->  
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
      <!--named slot -->
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>

      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
 
  </div>

  <div v-if="showModalTwo">
     <Modal @close="toggleModalTwo" theme="dark">
      <h1>Log In</h1>
      <br>
      <br>
      <form>
        <label for="username">Enter Your Username:</label>
        <br>
        <input type="text" name="username" placeholder="Username">
        <br>
        <br>
        <label for="password">Enter Your password:</label>
        <br>
        <input type="password" name="password" placeholder="Password">
      </form>
      <template v-slot:links>
        <a href="#">Log In</a>
        <a href="#">Register as a new User</a>
        
      </template>
    </Modal>
  </div>


  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <br>
  <br>
  <button @click="toggleModalTwo">Open Modal Two</button>
</template>

<script>
import Modal from './components/Modal'
export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'my First Vue App',
      header: 'Sign up for the Giveaway',
      text: 'Grab your ninja sawg for half price!',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    }
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
