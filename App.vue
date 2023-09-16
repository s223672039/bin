<template>
  <div>
    <!-- 6. List Rendering -->

    <!-- a. v-for with an Object -->
    <ul>
      <li v-for="(value, key) in myObject" :key="key">
        {{ key }}: {{ value }}
      </li>
    </ul>

    <!-- b. v-for with a Range -->
    <ul>
      <li v-for="n in 5" :key="n">{{ n }}</li>
    </ul>

    <!-- c. v-for on <template> -->
    <ul>
      <template v-for="item in items" :key="item.id">
        <li>{{ item.name }}</li>
      </template>
    </ul>

    <!-- d. v-for with v-if -->
    <ul>
      <li v-for="item in filteredItems" :key="item.id">
        {{ item.name }}
      </li>
    </ul>

    <!-- e. v-for with a Component -->
    <ul>
      <my-component v-for="item in itemsWithComponents" :key="item.id" :item="item"></my-component>
    </ul>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  data() {
    return {
      // Sample data for list rendering examples
      myObject: { key1: 'value1', key2: 'value2' },
      items: [
        { id: 1, name: 'Item 1' },
        { id: 2, name: 'Item 2' },
      ],
      itemsWithComponents: [
        { id: 1, name: 'Item 1' },
        { id: 2, name: 'Item 2' },
      ],
    };
  },
  computed: {
    // Computed property for filteredItems
    filteredItems() {
      return this.items.filter(item => item.condition);
    },
  },
  components: {
    // Define 'my-component' here if it's not already defined in your project
    // 'my-component': {
    //   props: ['item'],
    //   template: '<li>{{ item.name }}</li>'
    // }
  },
};
</script>
