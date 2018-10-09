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
  render(createElement, context) {
    const contentElement = createElement('span', {
      class: {
        'to-do-list-content': true,
        'finished': context.props.isFinished
      }
    }, [`• ${context.props.content}`]);

    const noop = () => {};
    const finishButton = createElement('button', {
      attrs: {
        type: 'button'
      },
      on: {
        click: () => context.listeners['finish']
          ? context.listeners['finish'](context.props.id)
          : noop
      }
    }, ['Finish']);

    const removeButton = createElement('button', {
      attrs: {
        type: 'button'
      },
      on: {
        click: () => context.listeners['remove']
          ? (context.props.id)
          : noop
      }
    }, ['Remove']);

    return createElement('li', {
      ...context.data,
      class: 'to-do-list-item'
    }, [contentElement, finishButton, removeButton])
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
