<template>
  <button
    type="submit"
    class="button"
    v-bind:class="{ button_transparent: transparent }"
  >
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: ["text", "transparent"],
};
</script>

<style scoped>
.button {
  width: 100%;

  padding: 20px;

  color: #ffffff;

  font-weight: 600;
  font-size: 18px;

  border: 0;
  border-radius: 8px;

  background-color: #667c89;

  cursor: pointer;
}

.button_transparent {
  color: var(--text);

  background-color: #ffffff;

  border: 3px solid #667c89;
}
</style>
