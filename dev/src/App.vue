<script setup>
import { RouterLink, RouterView } from 'vue-router';
import { ref } from 'vue'
let path = new ref(document.location.pathname)
function setPath(n) {
  path.value = n
}
let flags = ref({
})
let words = {
  secret : "secrets"
}
let wProg = {}

for (let key in words) {
  wProg[key] = 0
  flags.value[key] = false
}

document.onkeypress = function (e) {
    e /** @type {Event} */ = e || window.event;
    let letter = String.fromCodePoint(e.keyCode).toLowerCase()
    // use e.keyCode
    for (let key in words) {
      if (flags.value[key]) continue // already cleared
      let word = words[key]
      if (letter == word[wProg[key]]) {
        wProg[key]++
        if (word.length == wProg[key]) {
          flags.value[key] = true
        }
      } else {
        wProg[key] = 0
      }
    }
};

</script>

<template>
  <div class="container text-center" style="background-color: white; min-height: 100vh;">
    <div class="container container-fluid row border" style="background-color: floralwhite; width: stretch;">
      <div class="col text-end">
        <div class="float-start" style="margin:auto">
          <RouterLink to="/" class="nav-link m-1" v-on:click="() => setPath('/')"><img src="./assets/title.png" class="align-middle" style="height:10vh"></RouterLink>
        </div>
      </div>
      <div class="col text-start" style="align-content: center;">
        <nav class="btn-group align-middle align-end" style="margin:auto">
          <button type="button" :class="'btn btn-sm ' + (path == '/' ? 'btn-primary' : 'btn-secondary')"><RouterLink to="/" class="nav-link m-1" v-on:click="() => setPath('/')">Home</RouterLink></button>
          <button type="button" :class="'btn btn-sm ' + (path == '/about' ? 'btn-success' : 'btn-secondary')"><RouterLink to="/about" class="nav-link m-1" v-on:click="() => setPath('/about')">About</RouterLink></button>
          <button type="button" :class="'btn btn-sm ' + (path == '/team' ? 'btn-warning' : 'btn-secondary')"><RouterLink to="/team" class="nav-link m-1" v-on:click="() => setPath('/team')">Team</RouterLink></button>
          <button type="button" :class="'btn btn-sm ' + (path == '/game' ? 'btn-info' : 'btn-secondary')"><RouterLink to="/game" class="nav-link m-1" v-on:click="() => setPath('/game')">Game</RouterLink></button>
          <button type="button" v-if="flags.secret" :class="'btn btn-sm ' + (path == '/secret' ? 'btn-dark' : 'btn-secondary')"><RouterLink to="/secret" class="nav-link m-1" v-on:click="() => setPath('/secret')">Secret</RouterLink></button>
        </nav>
      </div>
    </div>
    <div class="d-flex justify-content-center"> <RouterView /></div>
  </div>
</template>

<style scoped>
a.nav-link {
}
a.router-link-active {

}
</style>
