<template>
  <div id="app">
    <with-keyboard-control :listLength="$options.list.length" @selected="selectedHandler">
      <template slot-scope="{selectedIndex}">
        <div
          v-for="(item, index) in $options.list"
          class="list-item"
          :class="{'selected': index === selectedIndex}"
          :key="index">
          <p>{{item}}</p>
        </div>
      </template>
    </with-keyboard-control>
  </div>
</template>

<script>
import WithKeyboardControl from "./components/WithKeyboardControl";
export default {
  name: "app",
  components: {
    WithKeyboardControl
  },
  methods: {
    selectedHandler(selectedIndex) {
      alert(
        `The item '${
          this.$options.list[selectedIndex]
        }' with index ${selectedIndex} has been selected!`
      );
    }
  },
  created() {
    this.$options.list = ["hello", "world", "this", "is", "a", "list"];
  }
};
</script>

<style lang="scss">
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 100vh;
}
.list-item {
  width: 150px;
  text-align: center;
  border: 1px solid #999;
  cursor: pointer;
}

.list-item:hover,
.list-item.selected {
  background-color: yellowgreen;
}
</style>
