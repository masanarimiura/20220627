<template>
  <div class="about">
    <div class="about" v-for="team in teams" :key="team">
      <h2 v-show="teamId===team.id">current team: {{team.name}}</h2>
    </div>
    <button @click="increase">counter</button>
    <p>{{ $store.state.sum }}</p>
    <p>Last team name clicked: {{ $store.state.lastTeam }}</p>
    <router-link to="/">戻る</router-link>
  </div>
</template>


<script>
export default {
  data() {
    return {
      teams: [
        {
          id: "c36136ef-552f-4dc9-84b6-65ecb8574e81",
          name: "Team_A",
        },
        {
          id: "ed0459f5-716d-4ef4-99ba-5dc750dfe0d0",
          name: "Team_B",
        },
        {
          id: "60d0d5d5-8ce9-41d9-a65b-13a090c10ae1",
          name: "Team_C",
        },
      ],
    };
  },
  teamName: {},
  props: ['teamId'],
  methods: {
    increase() {
      this.$store.commit('incrementMutation');
      this.$store.commit('lastTeamUpdateMutation', this.teamName.name);
    },
    getTeamName() {
      this.teams.forEach((team) => {
        if (team.id === this.teamId) {
          this.teamName = team;
        }
      });
    },
  },
  created() {
    this.getTeamName();
  }
};
</script>
