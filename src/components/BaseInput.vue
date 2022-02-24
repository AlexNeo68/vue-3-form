<template>
  <label v-if="label">{{ label }}</label>
  <input
    :value="modelValue"
    :type="type"
    v-bind="$attrs"
    :placeholder="label"
    class="field"
    @input="($event) => $emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  name: "BaseInput",
  props: {
    label: String,
    type: { type: String, default: "text" },
    modelValue: {
      type: [String, Number],
      default: "",
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
