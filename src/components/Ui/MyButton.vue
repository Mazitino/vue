<template>
  <button class="btn">
      <slot></slot>
  </button>
</template>

<script>
export default {
    name: 'my-button'

}
</script>

<style>
.btn {
    margin: 5px;
    padding: 15px 30px;
    background: none;
    color: teal;
    border: 1px solid teal;
}
</style>