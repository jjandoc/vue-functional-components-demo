<script>
export default {
  functional: true,
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
  },
  render(h, { props, listeners, data }) {
    const noop = () => {};
    const finishHandler = () => listeners['finish']
        ? listeners['finish'](props.id)
        : noop;
    const removeHandler = () => listeners['remove']
        ? listeners['remove'](props.id)
        : noop;

    return (
      <li class="to-do-list-item" {...data}>
        <span
            class={{
              'to-do-list-content': true,
              'finished': props.isFinished
            }}>
          • { props.content }</span>
        <button
            type="button"
            onClick={finishHandler}>
          Finish</button>
        <button
            type="button"
            onClick={removeHandler}>
          Remove</button>
      </li>
    );
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
