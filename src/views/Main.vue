<template>
    <div class="main-component">
        <ul>
            <li v-for="participant in participants">{{participant.name}}: {{participant.level}}</li>
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
  },
  data() {
    return {
      partName: '',
      partLevel: '',
      participants: [
        { name: 'Grzegorz', level: 'beginner' },
        { name: 'Tomasz', level: 'beginner' },
        { name: 'Paweł', level: 'beginner' },
        { name: 'Andżelika', level: 'beginner' },
        { name: 'Eric', level: 'beginner' },
      ],
    };
  },
  methods: {
    clickHandler() {
      const part = {
        name: this.partName,
        level: this.partLevel,
      };
      this.participants.push(part);
      this.partName = '';
      this.partLevel = '';
    },
  },
};
</script>

<style scoped>
    .main-component {
    }
</style>
