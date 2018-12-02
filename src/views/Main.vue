<template>
    <div class="main-component">
        <ul>
            <li v-for="participant in participantsList">
                {{participant.name}}: {{participant.level}}
            </li>
        </ul>
        <input v-model="partName"/>
        <input v-model="partLevel"/>
        <button :disabled="!isValid" @click="clickHandler()">Add to list</button>
    </div>
</template>

<script>
export default {
  name: 'main',
  computed: {
    isValid() {
      return this.partName !== '' && this.partLevel !== '';
    },
    participantsList() {
      return this.$store.state.app.participants;
    },
  },
  data() {
    return {
      partName: '',
      partLevel: '',
    };
  },
  methods: {
    clickHandler() {
      const part = {
        name: this.partName,
        level: this.partLevel,
      };
      this.$store.commit('add-participant', part);
    },
  },
};
</script>

<style scoped>
    .main-component {
    }
</style>
