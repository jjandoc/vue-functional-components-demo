<template functional>
  <li class="to-do-list-item">
    <span :class="['to-do-list-content', props.isFinished ? 'finished' : null]">
      • {{ props.content }}
    </span>
    <button
      type="button"
      @click="() => listeners['finish']
        ? listeners['finish'](props.id)
        : () => {}">Finish</button>
    <button
      type="button"
      @click="() => listeners['remove']
        ? listeners['remove'](props.id)
        : () => {}">Remove</button>
  </li>
</template>

<script>
export default {
  props: {
    content: {
      type: String,
      required: true
    },
    id: {
      type: Number,
      required: true
    },
    isFinished: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style>
.to-do-list-item {
  align-items: flex-end;
  display: flex;
  font-size: 22px;
  margin-bottom: .5em;
}

.to-do-list-content {
  flex-grow: 1;
}

.to-do-list-content.finished {
  text-decoration: line-through;
}

.to-do-list-item button {
  margin-left: 10px;
}
</style>
