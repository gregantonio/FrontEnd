<template>
  <button
    class="ft-button"
    :class="{'big': big, 'secondary': priority === 'secondary'}"

  >
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    big: {
      type: Boolean,
      default: () => false,
    },
    priority: {
      type: String,
      default: () => "primary"
    }
  },
  data() {
      return {
          users: [],
          numberOfUsers: 0
      }
  },
}
</script>

<style scoped>
.ft-button {
  background-color: var(--input-color);
  color: white;
  border: 1px solid var(--input-color);
  padding: 3px 12px;
  border-radius: 15px;
  transition: all var(--input-quick);
  box-shadow: 0 10px rgb(70, 70, 70);
}

.ft-button.big {
  font-size: 18px;
  width: 50%;
  padding: 5px 18px;
}

.ft-button.secondary {
  background-color: transparent;
  color: var(--input-color);
}

.ft-button:hover {
  background-color: var(--input-color-light);
  border-color: var(--input-color-light);
  /* box-shadow: 0 8px 16px 17px rgba(0, 0, 0, 0.2); */

}

.ft-button:active {
  background-color: #ba6ddd;
  box-shadow: 0 2px rgb(0, 0, 0);
  transform: translateY(6px);
}

.ft-button.secondary:hover {
  background-color: var(--shade-light);
}
</style>
