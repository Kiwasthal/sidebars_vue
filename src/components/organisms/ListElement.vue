<template>
  <Transition>
    <ul :class="listClasses" v-if="this.isOpen">
      <SidebarListItem
        v-for="listItem in listItems"
        :properties="listItem"
        :isSidebarElement="checkSidebar"
        :isDropDownElement="checkDropDown"
      />
    </ul>
  </Transition>
</template>

<script>
import SidebarListItem from '../molecules/SidebarListItem.vue';
import { emitter } from '../../helper/emitter';
export default {
  props: {
    listItems: {
      type: Object,
      required: true,
    },
    isSidebar: {
      type: Boolean,
      default: false,
    },
    isDropdown: {
      type: Boolean,
      default: false,
    },
  },
  components: {
    SidebarListItem,
  },
  data() {
    return { isOpen: true };
  },
  computed: {
    checkSidebar() {
      return this.isSidebar ? true : false;
    },
    checkDropDown() {
      return this.isDropdown ? true : false;
    },
    listClasses() {
      return this.checkSidebar
        ? 'fixed left-0 top-0 w-16 md:w-64 h-screen bg-white border-gray-300 border-t-2'
        : this.checkDropDown
        ? 'fixed top-20 right-6 bg-white origin-top p-3 rounded-lg'
        : '';
    },
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
  },
  created() {
    if (this.isDropdown) {
      emitter.on('toggle-dropdown', this.toggleDropdown);
    }
  },
};
</script>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
