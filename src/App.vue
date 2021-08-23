<template>
  <div>
    <button @click="additem">add item</button>
    <gridstack
      :griditems="items"
      @added="logger"
      @dragstart="logger"
      @resizestop="logger"
    />
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import gridstack from "./components/gridstack.vue";
export default {
  components: {
    gridstack,
  },
  setup() {
    const items = ref([
      { x: 2, y: 0, h: 1 },
      { x: 0, y: 2, w: 4 },
      { x: 3, y: 1, h: 1 },
      { x: 3, y: 0, h: 1 },
      { x: 0, y: 0, w: 2, h: 1 },
    ]);

    function additem() {
      const node = {
        x: Math.round(12 * Math.random()),
        y: Math.round(5 * Math.random()),
        w: Math.round(1 + 3 * Math.random()),
        h: Math.round(1 + 3 * Math.random()),
      };
      items.value.push(node);
    }

    function logger(evt) {
      console.log(evt);
    }

    return {
      logger,
      items,
      additem,
    };
  },
};
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
