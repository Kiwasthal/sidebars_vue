<template>
  <img :src="iconSrc" alt="" :class="itemClasses" />
</template>

<script>
export default {
  props: {
    iconSrc: String,
    elementType: String,
  },
  computed: {
    itemClasses() {
      switch (this.elementType) {
        case 'sidebar':
          return 'w-7 h-7';
        case 'dropdown':
          return 'w-7 h-7 bg-slate-200 rounded-full p-1';
      }
    },
  },
};
</script>
