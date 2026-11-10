<script setup>
const teamMembers = [
  {
    Name:"Angelo Schreiner",
    Tasks:["Programmer"],
    Desc:"Optimizes stuff i guess."
  },
  {
    Name:"Asefa Mirzad",
    Tasks:["Designer","Artist"],
    Desc:"Handles the Sketching and designing of the enemies."
  },
  {
    Name:"Johannes Grieshofer",
    Tasks:["Programmer","AI Engineer"],
    Desc:"Bro makes a majority of the game function via AI :P."
  },
  {
    Name:"Alexander Kaczmarczyk",
    Tasks:["Designer","Artist"],
    Desc:"Guy designing the UI and Stuff."
  }
]
</script>

<template>
  <div style="display:flex">
    <div class="card" style="width: 18rem; height: 100%" v-for="member of teamMembers">
      <img class="card-img-top" src="../../public/img/Standin.png" alt="Card image cap">
      <div class="card-body">
        <h5 class="card-title">{{member.Name}}</h5>

        <p class="card-text">{{ member.Desc }}</p>
      </div>
    </div>
  </div>
</template>
