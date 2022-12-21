<template>
  <UserBadge>
    <img
      src="https://via.placeholder.com/50x50"
      class="h-12 w-12 rounded-full"
      alt=""
    />
  </UserBadge>
  <div class="w-screen h-screen bg-slate-200 relative"></div>
  <ListElement :listItems="listItems" :isSidebar="true" />
  <ListElement :listItems="listItems" :isDropdown="true" />
</template>

<script>
import UserBadge from './components/atoms/UserBadge.vue';
import ListElement from './components/organisms/ListElement.vue';
import userIcon from './assets/usericon.svg';
import bellIcon from './assets/bellicon.svg';
import heartIcon from './assets/hearticon.svg';
import noteIcon from './assets/notesicon.svg';
import homeIcon from './assets/homeicon.svg';
import hiddenIcon from './assets/hidden.svg';
export default {
  name: 'App',
  components: {
    ListElement,
    UserBadge,
  },
  data() {
    return {
      listItems: [
        {
          icon: userIcon,
          label: 'My Profile',
        },
        {
          icon: bellIcon,
          label: 'Saved Searches',
        },
        {
          icon: heartIcon,
          label: 'Favorite listings',
        },
        {
          icon: noteIcon,
          label: 'Noted listings',
        },
        {
          icon: homeIcon,
          label: 'My Homes',
        },
        {
          icon: hiddenIcon,
          label: 'Hidden Listings',
        },
      ],
    };
  },
};
</script>

<style scoped></style>
