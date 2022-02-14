<template>
  <h3>单音练习</h3>
  <SingleNote @play="play" v-for="note in notes" :key="note.id" :note="note" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Sound from "./modules/Sound";
import SingleNote from "./components/SingleNote.vue";
import notes from "./data/notes";
import { Note } from "./interface/note";
let context = new (window.AudioContext || (window as any).webkitAudioContext)();
const sound = new Sound(context);

export default defineComponent({
  name: "App",
  setup() {
    const play = (note: Note) => {
      let value = note.frequency;
      sound.play(value);
      sound.stop();
    };
    return {
      notes,
      play,
    };
  },
  components: {
    SingleNote,
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
