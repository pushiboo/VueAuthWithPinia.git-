<script setup>
import { RouterLink } from 'vue-router'
import { useNavStore } from '../stores/nav.store'
import { useAuthStore } from '@/stores/auth.store.js'
import { useDark, useToggle } from '@vueuse/core'
import { onUpdated } from 'vue'

const isDark = useDark()
const toggleDark = useToggle(isDark)
// const authStore = useAuthStore()
// const updateUser = authStore
// authStore.$patch({
//   storeUser: '',
//   storeEmail: ''
// })

const getUserstate = useAuthStore()
const darkMode = useNavStore()

console.log("authStore:" ,getUserstate.$state);
// onUpdated(() => {
//   getUserstate.$state
//   // text content should be the same as current `count.value`
//   // console.log("getUserstate",getUserstate)
// })

/* console.log("get store value: darkMode", darkMode) */
console.log("get store value: darkMode.getDarkMode", darkMode.getDarkMode)
/* console.log("get store value: darkMode.toogleDarkMode", darkMode.toggleDarkMode) */
</script>

<template>
  <div>
    <nav>
        <div>
          <RouterLink to="/">Home</RouterLink>
          <RouterLink to="/register">Register</RouterLink>
          <RouterLink to="/login">Login</RouterLink>
          <RouterLink to="/logout">Logout</RouterLink>

        </div>
        <div>
          <!-- <span v-if="getUserstate">---- {{ getUserstate.$state.storeUserName }} ---</span> -->
          <span class=" flex flex-col justify-end font-italic text-pink-darken-3">{{ getUserstate.$state.storeUserEmail  }}</span>
        </div>
        <!-- <v-checkbox label="Checkbox"></v-checkbox> -->
        <div @click="darkMode.toggleDarkMode" class="flex flex-col justify-center">
          <div v-if="darkMode.getDarkMode">        
            <svg class="hidden dark:block" width="16" height="16" xmlns="http://www.w3.org/2000/svg">
            <path class="fill-slate-300" d="M7 0h2v2H7zM12.88 1.637l1.414 1.415-1.415 1.413-1.413-1.414zM14 7h2v2h-2zM12.95 14.433l-1.414-1.413 1.413-1.415 1.415 1.414zM7 14h2v2H7zM2.98 14.364l-1.413-1.415 1.414-1.414 1.414 1.415zM0 7h2v2H0zM3.05 1.706 4.463 3.12 3.05 4.535 1.636 3.12z" />
            <path class="fill-slate-400" d="M8 4C5.8 4 4 5.8 4 8s1.8 4 4 4 4-1.8 4-4-1.8-4-4-4Z" />
          </svg>
          </div>
          <div v-else>
            <svg class="hidden dark:block" width="16" height="16" xmlns="http://www.w3.org/2000/svg">
              <path class="fill-slate-400" d="M6.2 1C3.2 1.8 1 4.6 1 7.9 1 11.8 4.2 15 8.1 15c3.3 0 6-2.2 6.9-5.2C9.7 11.2 4.8 6.3 6.2 1Z" />
              <path class="fill-slate-500" d="M12.5 5a.625.625 0 0 1-.625-.625 1.252 1.252 0 0 0-1.25-1.25.625.625 0 1 1 0-1.25 1.252 1.252 0 0 0 1.25-1.25.625.625 0 1 1 1.25 0c.001.69.56 1.249 1.25 1.25a.625.625 0 1 1 0 1.25c-.69.001-1.249.56-1.25 1.25A.625.625 0 0 1 12.5 5Z" />
            </svg>
          </div>
        </div>
    </nav>
  </div>
</template>

<style>
nav {
  @apply 
  w-full
  text-xs
  text-center
 /*  my-8 */
  flex justify-between
  px-4
  border
  border-teal-500
  p-2
  
}
nav a.router-link-exact-active {
  @apply 
    text-indigo-500
}

nav a.router-link-exact-active:hover {
  @apply 
    bg-transparent
}
nav a {
  @apply 
    inline-block
    pr-4 p-0
    border-l-indigo-500
}
nav a:first-of-type {
  @apply 
    border-none
}
</style>