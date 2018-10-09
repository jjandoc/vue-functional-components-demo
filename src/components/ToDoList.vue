<template>
  <ul class="to-do-list">
    <ToDoListItem
        v-for="item in items"
        :key="item.id"
        v-bind="item"
        @finish="$emit('finish', $event)"
        @remove="$emit('remove', $event)" />
  </ul>
</template>

<script>
import ToDoListItem from '@/components/ToDoListItem.vue'
// import ToDoListItem from '@/components/FunctionalToDoListItem.vue'
// import ToDoListItem from '@/components/FunctionalJsxToDoListItem.vue'
// import ToDoListItem from '@/components/FunctionalTemplateToDoListItem.vue'

export default {
  components: { ToDoListItem },
  props: {
    items: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style>
.to-do-list {
  list-style: none;
  padding: 0;
}
</style>
