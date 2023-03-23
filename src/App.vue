
<script setup lang="ts">
// import Button from './components/Button.vue'
import { computed, ref, onMounted } from 'vue'
import { useModal } from './composables/modal'

const modalStyle = computed(() => {
  return {
    display: modal.show.value ? 'block' : 'none'
  }
})
const mounted = ref(false);
onMounted(() => {
  mounted.value = true;
});

const modal = useModal()
console.log("Modal = ", modal)


</script>
<template>
  <div>
    <main>
      <div class="grid h-screen place-items-center">
        <div>
          <!-- <Button @click="modal.showModal('signIn')" /> -->
          <button class="button" @click="modal.showModal('signUp')">Sign Up</button>
          <button class="button" @click="modal.showModal('signIn')">Sign In</button>
        </div>
        <div class="modal" style="color: black;" :style="modalStyle">
          <div class="modal-background">
            <div class="modal-content">
              <div id="newid">
                test
              </div>
            </div>
          </div>
          <button class="modal-close is-large" @click="modal.hideModal()"></button>
        </div>
      </div>

      <div v-if="mounted">
        <Teleport to="#newid">
          <!-- checking -->
          <component :is="modal.component.value" />
        </Teleport>
      </div>


    </main>
  </div>
</template>


<style>
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css";
@import "highlight.js/styles/atom-one-dark.css";
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */

/* .btn {
  @apply font-bold py-2 px-4 rounded;
}

.btn-blue {
  @apply bg-blue-500 text-white;
}

.btn-blue:hover {
  @apply bg-blue-700;
}

.button{
  margin: 15px;
} */
</style>
