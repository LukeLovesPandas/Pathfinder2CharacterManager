<template>
    <div class="stats_block"> 
      <p>{{capitalizedName()}}: {{statValue}}</p>
      <button v-on:click="$emit('increaseStat', statName)" v-bind:disabled="increaseDisabled()">+</button>      
      <button v-on:click="$emit('decreaseStat', statName)" v-bind:disabled="decreaseDisabled()">-</button>
    </div>  
</template>

<script>
export default {
  name: 'StatBlock',
  props: ['statName', 'statValue'],
  methods: {
    capitalizedName(){
      return this.statName.replace(this.statName[0], this.statName[0].toUpperCase());
    },
    decreaseDisabled() {
      return this.statValue <= 8
    },
    increaseDisabled() {
      return this.statValue >= 22
    },
  }
}
</script>

<style scoped>
  .stats_block {
    margin: 1.5em;
  }
</style>


