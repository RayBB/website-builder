<template>
  <div class="Section">
      <h2>{{heading}}</h2>
      <div class="Items">
          <!-- To work with different component types we'll liekly need to pass in things other than just name and description. -->
        <component v-bind:is="item.type" v-for="item in items" :key="item.name" :name="item.name" :description="item.description"></component>
      </div>
  </div>
</template>

<script>
import BasicItem from './BasicItem.vue'

export default {
  name: 'Section',
  props: {
      heading: String,
      items: Array
  },
  components: {
    BasicItem
  }
}
</script>

<style>
.Section {
  border: 1px dotted rgb(0, 90, 35);
}
.Items {
  display: inline-flex;
}
</style>
