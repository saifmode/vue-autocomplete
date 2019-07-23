<template>
  <div id="app">
    <autocomplete :data="data" @selected="selected = $event"></autocomplete>
    <p>Selected item: {{ selected }}</p>
  </div>
</template>

<script>
import Autocomplete from "./components/Autocomplete.vue";

export default {
  name: "app",
  components: {
    autocomplete: Autocomplete
  },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      data: [
        "Apples",
        "Apricots",
        "Avocados",
        "Bananas",
        "Boysenberries",
        "Blueberries",
        "Bing Cherry",
        "Cherries",
        "Cantaloupe",
        "Crab apples",
        "Clementine",
        "Cucumbers",
        "Damson plum",
        "Dinosaur Eggs",
        "Dates",
        "Dewberries",
        "Dragon Fruit",
        "Elderberry",
        "Eggfruit",
        "Evergreen Huckleberry",
        "Entawak",
        "Fig",
        "Farkleberry",
        "Finger Lime",
        "Grapefruit",
        "Grapes",
        "Gooseberries",
        "Guava",
        "Honeydew melon",
        "Hackberry",
        "Honeycrisp Apples",
        "Indian Prune",
        "Indonesian Lime",
        "Imbe",
        "Indian Fig",
        "Jackfruit",
        "Java Apple",
        "Jambolan",
        "Kiwi",
        "Kaffir Lime",
        "Kumquat",
        "Lime",
        "Lemon",
        "Longan",
        "Lychee",
        "Loquat",
        "Mango",
        "Mandarin Orange",
        "Mulberry",
        "Melon",
        "Nectarine",
        "Navel Orange",
        "Nashi Pear",
        "Olive",
        "Oranges",
        "Ogeechee Limes",
        "Oval Kumquat",
        "Papaya",
        "Persimmon",
        "Paw Paw",
        "Prickly Pear",
        "Peach",
        "Pomegranate",
        "Pineapple",
        "Quince",
        "Queen Anne Cherry",
        "Quararibea cordata",
        "Rambutan",
        "Raspberries",
        "Rose Hips",
        "Star Fruit",
        "Strawberries",
        "Sugar Baby Watermelon",
        "Tomato",
        "Tangerine",
        "Tamarind",
        "Tart Cherries",
        "Ugli Fruit",
        "Uniq Fruit",
        "Ugni",
        "Vanilla Bean",
        "Velvet Pink Banana",
        "Voavanga",
        "Watermelon",
        "Wolfberry",
        "White Mulberry",
        "Xigua",
        "Ximenia caffra fruit",
        "Xango Mangosteen Fruit Juice",
        "Yellow Passion Fruit",
        "Yunnan Hackberry",
        "Yangmei",
        "Zig Zag Vine fruit",
        "Zinfandel Grapes",
        "Zuchinni"
      ],
      selected: ""
    };
  }
};
</script>

<style></style>
