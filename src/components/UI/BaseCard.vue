<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'BaseCard',
};
</script>

<style scoped>
div {
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  margin: 2rem auto;
  max-width: 40rem;
}

.warn {
  color: #9f6000;
  background-color: #feefb3;
  font-size: 18px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(255, 201, 41, 0.1);
  border-radius: 4px;
  padding: 0.1rem;
}
</style>

.
