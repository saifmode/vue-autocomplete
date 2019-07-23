<template>
  <div id="autocomplete">
    <input
      type="text"
      v-model="input"
      
    />
    <ul>
      <li
        v-for="(item, i) in predictions"
        :key="`data-${i}`"
      >{{ item }}</li>
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
    }
  },
  computed: {
    predictions() {
      let searchItem = this.input.toLowerCase();
      let lettersInSearch = searchItem.length;
      let searchResults = [];
      if (lettersInSearch > 0) {
        searchResults = this.data.filter(item => {
          return searchItem == item.toLowerCase().split("").splice(0, lettersInSearch).join("")
        })
      } else {
        return [];
      }
      return searchResults
    }
  },
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
    margin: 0;
    padding: 0;
    width: 233px;
    list-style: none;
  }

  li {
    height: 21px;
    padding: 5px 8px;
    border: 1px solid #aaa;
  }
</style>
