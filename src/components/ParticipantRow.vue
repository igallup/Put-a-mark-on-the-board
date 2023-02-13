[<template>
      <tr>
        <td>
          {{ participant.name}}
        </td>
        <td>
          {{ participant.markCount }}
<!-- abandoned tally mark functionality, for now
    &nbsp;-->
<!--            <div v-for="mark in participant.markCount">{{ mark }}</div>-->
        </td>
        <td>
          <button @click="updateCount(1)">+</button>
        </td>
        <td>
          <button @click="updateCount(-1)">-</button>
        </td>
        <td>
          <button @click="$emit('removeParticipant', participant.name)">Forgive and forget</button>
        </td>
      </tr>
</template>
// Need a list of names to iterate over
<script>
export default {
  props: {
    participant: {type: Object},
  },
  emits: ['removeParticipant'],
  data: () => ({}),
  methods: {
    updateCount(num) {
      this.participant.markCount += num;
      if (this.participant.markCount < 0) {
        this.participant.markCount = 0;
      };
    },

  }
}
</script>

<style>
button {
  text-align: center;
  width: 80px;
  background-color: greenyellow;
  border: 3px solid darkslategray;
  border-radius: 30px;
  color: black;
  font-weight: bold;
}

li {
  display: inline-block;
  height: 20px;
  border: 1px limegreen;
  margin-right: 4px;
  :nth-child(5n) {
   transform: rotate(300deg);
   height: 30px;
   position: relative;
   left: -15px;
   top: 5px;
   margin-right: 1em;
   margin-top: -10px;
   }
}
</style>