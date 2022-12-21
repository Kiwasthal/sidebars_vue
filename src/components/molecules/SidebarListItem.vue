<template>
  <li @click="showStripe = !showStripe" :class="listClasses">
    <div
      v-if="isSidebarElement"
      class="stripe bg-cyan-600"
      :class="{ 'stripe-animated': showStripe }"
    ></div>
    <SidebarElementIcon
      :iconSrc="properties.icon"
      :elementType="declareElementType"
    />
    <SidebarElementLabel
      :elementLabel="properties.label"
      :elementType="declareElementType"
    />
  </li>
</template>

<script>
import SidebarElementIcon from '../atoms/SidebarElementIcon.vue';
import SidebarElementLabel from '../atoms/SidebarElementLabel.vue';

export default {
  props: {
    properties: Object,
    isSidebarElement: Boolean,
    isDropDownElement: Boolean,
  },
  components: {
    SidebarElementIcon,
    SidebarElementLabel,
  },
  data() {
    return {
      showStripe: false,
    };
  },
  computed: {
    declareElementType() {
      return this.isSidebarElement
        ? 'sidebar'
        : this.isDropDownElement
        ? 'dropdown'
        : 'default';
    },
    listClasses() {
      return this.isSidebarElement
        ? 'justify-center md:justify-start flex gap-3 items-center p-4 cursor-pointer relative hover:bg-gray-100 transition-colors duration-300 border-b-2 border-gray-200'
        : this.isDropDownElement
        ? 'flex gap-3 items-center p-4 cursor-pointer relative hover:bg-gray-100 transition-colors duration-300'
        : 'default';
    },
  },
};
</script>

<style>
.stripe {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 4px;
  transition: top 0.3s ease-in-out;
  top: 100%;
}

.stripe-animated {
  top: 0;
}
</style>
