<!-- This is the viewer of all the sections seen on the right side -->
<template>
  <div class="Preview">
      <Section v-for="section of sections" :key="section.heading" :heading="section.heading" :items="section.items" />
  </div>
</template>

<script>
import Section from './Section.vue'

export default {
  name: 'Preview',
  props: {
      sections: Array
  },
  components: {
    Section
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
