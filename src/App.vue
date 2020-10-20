<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <form
    @submit.prevent="handleSubmit"
  >
    <label for="name">Name</label>
    <input-simple 
      class="input-class"
      type="text" 
      placeholder="Ivan Ivanov"
      v-model="user.name"
      @change="handleNameChange($event.target.value)"
      required
    />
    <label for="name">E-mail</label>
    <input-simple 
      class="input-class"
      name="email"
      type="email"
      placeholder="ivan@example.com"
      v-model="user.email"
      required
    />
    <p class="user-info-header">
      Still reactive:
    </p>
    <p class="user-info">
      Your name: {{ user.name }}
    </p>
    <p class="user-info">
      Your email: {{ user.email }}
    </p>
    <button type="submit">Submit</button>
  </form>
</template>

<script>
import InputSimple from './components/InputSimple.vue';

export default {
  name: 'App',
  components: {
    InputSimple,
  },
  data() {
    return {
      user : {
        name: 'Vasya Krolikov',
        email: '',
      }
    }
  },
  methods: {
    handleSubmit() {
      window.alert('Submitted')
    },
    handleNameChange(value) {
      window.alert(`You've just changed your name to "${value}"`);
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

form {
  width: 360px;
  border: 1px solid lightblue;
  border-radius: 12px;
  padding: 24px;
  margin: 0 auto;
  text-align: left;
}

label {
  font-weight: bold;
  display: block;
  margin-bottom: 4px;
}

.input-class {
  margin-bottom: 12px;
}

.user-info {
  font-weight: bold;
}

.user-info-header {
  font-size: 18px;
  text-align: center;
}
</style>
