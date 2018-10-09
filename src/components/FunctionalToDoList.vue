<script>
import ToDoListItem from '@/components/FunctionalJsxToDoListItem.vue'

export default {
  functional: true,
  props: {
    items: {
      type: Array,
      default: () => []
    }
  },
  render(h, { props, listeners, data }) {
    const noop = () => {};
    const finishHandler = (e) => listeners['finish']
        ? listeners['finish'](e)
        : noop;
    const removeHandler = (e) => listeners['remove']
        ? listeners['remove'](e)
        : noop;
    
    return(
      <ul class="to-do-list">
        {props.items.map(item => (
          <ToDoListItem
              key={item.id}
              onFinish={finishHandler}
              onRemove={removeHandler}
              id={item.id}
              content={item.content}
              isFinished={item.isFinished} />)
        )}
      </ul>
    )
  }
}
</script>

<style>
.to-do-list {
  list-style: none;
  padding: 0;
}
</style>
