<template>
  <form class="to-do-form" @submit.prevent="handleSubmit">
    <input type="text" placeholder="What to do..." v-model="input" />
    <button type="Submit">Add item</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      input: null
    }
  },
  methods: {
    handleSubmit() {
      this.$emit("add", this.input);
      this.input = null;
    }
  }
}
</script>

<style>
.to-do-form {
  display: flex;
  width: 100%;
}

.to-do-form input {
  flex-grow: 1;
  font-size: 18px;
  padding: 10px;
}

.to-do-form button {
  margin-left: 10px;
}
</style>
