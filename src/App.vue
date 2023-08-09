<script setup>
import { ref,reactive } from 'vue'


const users = reactive([
  { id: 1, username: 'johndoe', pass: '1234'},
  { id: 2, username: 'janedoe', pass: '1234'},
  { id: 3, username: 'admin', pass: '1234'}
]);

const username = ref('');
const password = ref('');
const confirmPassword = ref('');
const loginShow = ref(true);


/*
const login = () => {
  const user = users.find(user => user.username === username.value && user.pass === password.value);
  if (user) {
    alert('logged in');
  } else {
    alert('wrong username or password');
  }
}
*/

function login() {
  const user = users.find(user => user.username === username.value && user.pass === password.value);
  if (user) {
    alert('logged in');
    window.location.href = "https://github.com/kamrul07/vue-login";
  } else {
    alert('wrong username or password');
  }
}


function register() {
  const existingUser = users.find(user => user.username === username.value);
  
  if( (password.value == confirmPassword.value) && (password.value != '') && (confirmPassword.value != '')){
    if(existingUser){
     alert('username already exists');
  }else{
    
    users.push({id: users.length + 1, username: username.value, pass: password.value});
    alert('user created');

  }
  }else{
    alert('passwords do not match');
  }

}
</script>

<template>
  <section class="flex h-screen w-full">
    <div class="w-1/2" style="background-image: url(https://images.unsplash.com/photo-1690555575753-7aa27df96b52?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80); background-repeat: no-repeat; background-size: cover;">
      <h1 class="mb-5 text-2xl mt-10 ml-10 text-white">Kosmos!</h1>
    </div>
    <div class="w-1/2 flex flex-col justify-center items-center bg-gray-200">
      <h2 class="mb-5 text-xl">Login or register</h2>
      <div class="w-full max-w-xs">
        <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" :style="loginShow ? 'display:block' : ' display:none;'">
          <div class="mb-">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
              Username
            </label>
            <input v-model="username" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Username">
          </div>
          <div class="mb-6">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
              Password
            </label>
            <input v-model="password" class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="******************">
            <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
          </div>
          <div class="flex items-center justify-between">
            <button @click="login()" class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
              Sign In
            </button>
            <a @click="loginShow = !loginShow " class="inline-block align-baseline font-bold text-sm text-orange-600 hover:text-orange-800" href="#">
              Or Register
            </a>
          </div>
        </form>
        <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" :style="!loginShow ? 'display:block' : ' display:none;'">
          <div class="mb-">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
              Username
            </label>
            <input v-model="username" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Username">
          </div>
          <div class="mb-6">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
              Password
            </label>
            <input v-model="password" class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="******************">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
              Confirm Password
            </label>
            <input v-model="confirmPassword" class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="******************">
            <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
          </div>
          <div class="flex items-center justify-between">
            <button @click="register()" class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
              Register
            </button>
            <a @click="loginShow = !loginShow " class="inline-block align-baseline font-bold text-sm text-orange-600 hover:text-orange-800" href="#">
              Or login
            </a>
          </div>
        </form>
        <p class="text-center text-gray-500 text-xs">
          &copy;2020 Acme Corp. All rights reserved.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
