<template>
  <button
    class="cursor-pointer bg-yellow-200 absolute top-5 right-5 rounded-full z-50"
    @click="toggleDropdown"
  >
    <slot></slot>
  </button>
</template>

<script>
import { emitter } from '../../helper/emitter';
export default {
  name: 'UserBadge',
  methods: {
    toggleDropdown() {
      emitter.emit('toggle-dropdown');
    },
  },
};
</script>
