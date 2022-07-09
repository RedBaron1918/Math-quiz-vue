<template>
  <button @click="$emit('SelectOperator', '+')">Addition<br />+</button>
  <button @click="$emit('SelectOperator', '-')">Subtraction<br />-</button>
  <button @click="$emit('SelectOperator', '/')">Division<br />/</button>
  <button @click="$emit('SelectOperator', '*')">Multiply<br />*</button>
</template>

<script>
export default {};
</script>

<style></style>
