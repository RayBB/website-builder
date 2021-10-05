<template>
  <div class="BasicItem">
    <strong>{{name}}</strong>
    <p>{{description}}</p>
  </div>
</template>

<script>

export default {
  name: 'BasicItem',
  props: {
      name: String,
      description: String
  }
}
</script>

<style>
.BasicItem {
  border: 1px solid red;
  width: 150px;
  margin: 1rem;
}
</style>
