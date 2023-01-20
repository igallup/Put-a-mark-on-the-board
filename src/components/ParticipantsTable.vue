<template>
  <div>

    <h1>{{ title}}</h1>
    <table>
      <tr>
        <th>Team Member</th>
        <th>Marks</th>
      </tr>
        <ParticipantRow v-for="participant in participants" v-bind:key="participant.name" :participant="participant" ></ParticipantRow>
    </table>
    <input v-model="newName" type="text" placeholder="New loser"><button @click="addParticipant()">Add new participant</button>
  </div>
</template>

// Need a list of names to iterate over
<script>
  import ParticipantRow from './ParticipantRow.vue'
  export default {
    components: {
      ParticipantRow
    },
    data: () => ({
      title: 'Put a Mark on the Board for',
        participants: [
          {"name":"Isaac", "markCount": 0},
          {"name":"Jacob", "markCount": 0}
        ],
        newName: '',
    }),
    methods: {
      addParticipant() {
        let newUser = {'name':this.newName, 'markCount':0}
        this.participants.push(newUser);
        }
    }
  }
</script>

<style>
</style>