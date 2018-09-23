<template>
  <div>
    <h2>Pathfinder 2E Stats Calculator</h2>
    <div class="stats_section">
      <StatBlock
        v-for="(value, key) in stats"
        v-bind:key="key"
        v-bind:statName="key"
        v-bind:statValue="value"
        v-on:increaseStat="increaseStat"
        v-on:decreaseStat="decreaseStat">
      </StatBlock>
    </div>
  </div>
</template>

<script>
import StatBlock from './StatBlock.vue'
export default {
  name: 'StatsCalculator',
  data: function () {
    return {
      stats: {
        strength: 10,
        dexterity: 10,
        constitution: 10,
        wisdom: 10,
        intelligence: 10,
        charisma: 10
      }
    }
  },
  methods: {
    increaseStat(key) {
      let statValue = this.stats[key];
      this.stats[key] = statValue >= 18 ? statValue + 1: statValue + 2;
    },
    decreaseStat(key) {
      let statValue = this.stats[key];
      this.stats[key] = statValue > 18  ? statValue -1 : statValue - 2;
    },
  },
  components: {
    StatBlock
  }

}
</script>

<style scoped>
  .stats_section {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .stats_block {
    margin: 1.5em;
  }
</style>
