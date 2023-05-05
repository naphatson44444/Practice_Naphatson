<template>
  <div>
    <p v-for="manu in manufacturer" :key="manu.id">
      {{ manu.id }} - {{ manu.Tiyle }}
    </p>
    <input placeholder="id" v-madel="id" />
    <input placeholder="Title" v-madel="Title" />
    <button @click="post()">Post</button>
    <button @click="put()">Put</button>
    <button @click="remove()">Delete</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      text: "test",
      manufacturer: [{ id: 1, Title: "test1" }],
      id: "",
      Title: "",
    };
  },
  created() {
    this.get();
  },
  methods: {
    get() {
      axios.get("https://localhost:7095/api/manufacturers").then((respone) => {
        this.manufacturer = respone.data;
      });
    },

    post() {
      axios
        .get("https://localhost:7095/api/manufacturers", {
          id: this.id,
          Title: this.Title,
        })
        .then((repone) => {
          this.get();
        });
    },

    remove() {
      axios
        .delete("https://localhost:7095/api/manufacturers" + this.id)
        .then((respone) => {
          this.get();
        });
    },
  },
};
</script>