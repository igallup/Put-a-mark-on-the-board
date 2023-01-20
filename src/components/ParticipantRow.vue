<template>
    <div>
      <tr>
        <td>
          {{ participant.name}}
        </td>
        <td>
          {{ participant.markCount }}
        </td>
        <td>
          <button @click="updateCount(participant, 1)">+</button>
        </td>
        <td>
          <button @click="updateCount(participant, -1)">-</button>
        </td>
        <td>
          <button>Forgive and forget</button>
        </td>
      </tr>
    </div>
</template>
// Need a list of names to iterate over
<script>
export default {
  props: {
    participant: {type: Object}
  },
  data: () => ({}),
  methods: {
    updateCount(participant, num) {
      participant.markCount += num;
      if (participant.markCount < 0) {
        participant.markCount = 0;
      };
    }
  }
}
</script>

<style>
</style>