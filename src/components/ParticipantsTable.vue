<template>
  <div>
    <table>
      <tr>
        <th>Team Member</th>
        <th>Marks</th>
      </tr>

      <tr v-for="item in items" v-bind:key="items.name">
        <td>
          {{ item.name}}
        </td>
        <td>
          {{ item.markCount }}
        </td>
        <td>
          <button @click="updateCount(item, 1)">+</button>
        </td>
        <td>
          <button @click="updateCount(item, -1)">-</button>
        </td>
        <td>
          <button>Forgive and forget</button>
        </td>
      </tr>
    </table>
    <input v-model="newName" type="text" placeholder="New loser"><button @click="addParticipant()">Add new participant</button>
  </div>
</template>
// Break out each row into its own component - i.e. from ParticipantRow.vue into this file
// Need a list of names to iterate over
<script>
  export default {
    data: () => ({
        title: 'Put a Mark on the Board for',
        items: [
          {"name":"Isaac", "markCount": 0},
          {"name":"Jacob", "markCount": 0}
        ],
        newName: '',
    }),
    methods: {
      addParticipant() {
        let newUser = {'name':this.newName, 'markCount':0}
        this.items.push(newUser);
        },
      updateCount(item, num) {

        item.markCount += num;
      }
  }
  }
</script>

<style>
</style>