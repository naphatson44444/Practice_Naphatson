<template>
  <div>
    <input v-model="text" />
    <button @click="goTohome()">Go</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "",
    };
  },
  methods: {
    goTohome() {
      this.$router.push({ path: "/", query: { msg: this.text } });
    },
  },
};
</script>