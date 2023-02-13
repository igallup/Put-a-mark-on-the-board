<template>
  <div>

    <h1>{{ title}}</h1>
    <div class="table-container">
<!--      flex layouts with divs instead of tables, trs, and tds-->
      <div>
        <div>Team Member</div>
        <div>Marks</div>

      </div>
        <ParticipantRow v-for="participant in participants" v-bind:key="participant.name" :participant="participant" @removeParticipant="removeParticipant" ></ParticipantRow>
    </div>
    <input v-model="newName" type="text" placeholder="New loser"><button class="resetBtn" @click="addParticipant()">Add new participant</button>
  </div>
</template>

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
        if (this.newName !== '') {
          this.participants.push(newUser);
          this.newName = ''
        }
        },
      removeParticipant(name) {
        const index = this.participants.findIndex(item => item.name === name);
        if (index > -1) {
          this.participants.splice(index, 1);
        }
      }
    }
  }
</script>

<style>
.table-container {
  display: flex;
  flex-direction: row;

  justify-content: space-around;
  flex-wrap: nowrap;
  align-items: stretch;
}
h1  {
  color: cadetblue;
}
td {
  text-align: center;
  color: white;
}
th {
  text-align: center;
  width: 220px;
  background-color: cadetblue;
  border: 3px solid darkslategray;
  border-radius: 5px;
  color: black;
  font-weight: bold;
}
.resetBtn {
  text-align: center;
  width: 220px;
  background-color: darkseagreen;
  border: 3px solid  darkslategrey;
  border-radius: 30px;
  color: black;
}
</style>