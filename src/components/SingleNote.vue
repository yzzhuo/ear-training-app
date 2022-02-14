<template>
  <b-button @click="onClick">{{ note.id }}</b-button>
</template>

<script>
import { toRefs } from "vue";

export default {
  name: "SingleNote",
  props: {
    note: Object,
  },
  emits: ["play"],
  setup(props, { emit }) {
    const { note } = toRefs(props);
    return {
      onClick: () => {
        emit("play", note.value);
      },
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
