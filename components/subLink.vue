<template>
  <div>
    <div v-if="Sublink.found">
      <a :href="Sublink.link">
        {{ Sublink.name }}
      </a>
    </div>
    <div v-else>{{ Sublink.name }} (No link found)</div>
  </div>
</template>

<script>
//imports
import MenuData from '~/static/OrderMenus.json';
export default {
  props: ['linkitem'],
  data: function () {
    return {
      item: this.linkitem,
      sublink: { found: false },
    };
  },

  computed: {
    Sublink() {
      const sublink = MenuData.find((el) => el.Name === this.item);

      let found = typeof sublink != 'undefined' ? true : false;
      let link =
        typeof sublink != 'undefined' ? sublink.Name.replace(/\W/g, '_') : null;
      return {
        found,
        name: this.item,
        link,
      };
    },
  },
};
</script>

<style></style>
