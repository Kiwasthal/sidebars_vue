<template>
  <span :class="itemClasses">{{ elementLabel }}</span>
</template>

<script>
export default {
  props: {
    elementLabel: String,
    elementType: String,
  },
  computed: {
    itemClasses() {
      switch (this.elementType) {
        case 'sidebar':
          return 'hidden md:block text-lg text-gray-800"';
        case 'dropdown':
          return 'text-lg text-gray-800';
      }
    },
  },
};
</script>
