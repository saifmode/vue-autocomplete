<template>
  <div>
    <input
      type="text"
      v-model="input"
      @keydown.down.prevent="down"
      @keydown.up.prevent="up"
      @keydown.enter.prevent="selectEnter"
    />
    <ul>
      <li
        v-for="(item, i) in predictions"
        :key="`data-${i}`"
        :class="{ selected: i === selectedIndex }"
        @click="selectClick"
      >
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    data: { type: Array }
  },
  data() {
    return {
      input: "",
      selectedIndex: -1
    };
  },
  computed: {
    predictions() {
      let searchItem = this.input.toLowerCase();
      let lettersInSearch = searchItem.length;
      let searchResults = [];
      if (lettersInSearch > 0) {
        searchResults = this.data.filter(item => {
          return (
            searchItem ==
              item
                .toLowerCase()
                .split("")
                .splice(0, lettersInSearch)
                .join("") && this.input != item
          );
        });
      } else {
        return [];
      }
      if (searchResults.length <= this.selectedIndex) {
        this.selectedIndex = -1;
      }
      return searchResults;
    }
  },
  methods: {
    down() {
      if (this.predictions) {
        this.selectedIndex += 1;
        this.selectedIndex = this.selectedIndex % this.predictions.length;
        this.$emit("selection-hover", this.predictions[this.selectedIndex]);
      }
    },
    up() {
      if (this.predictions) {
        this.selectedIndex -= 1;
        this.selectedIndex =
          (this.selectedIndex + this.predictions.length) %
          this.predictions.length; // prevents negative index which would cause modulo wrap to fail
        this.$emit("selection-hover", this.predictions[this.selectedIndex]);
      }
    },
    selectEnter() {
      this.input = this.predictions[this.selectedIndex];
      this.select();
    },
    selectClick() {
      this.input = event.target.innerText;
      this.select();
    },
    select() {
      this.$emit("selected", this.input);
    }
  }
};
</script>

<style>
input[type="text"] {
  width: 233px;
  height: 21px;
  padding: 5px 8px;
  outline: none;
}

ul {
  display: flex;
  flex-direction: column;
  position: absolute;
  margin: 0;
  padding: 0;
  width: 233px;
  list-style: none;
}

li {
  height: 21px;
  padding: 5px 8px;
  border: 1px solid #aaa;
  background-color: white;
}

li:hover {
  background-color: #bbbbbb;
}

.selected {
  background-color: #ddddfb;
}
</style>
