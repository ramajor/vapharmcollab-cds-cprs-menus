<template>
  <b-col>
    <div class="my-3" v-for="item in Items" :key="item.index">
      <div v-if="item.Header === 1">
        <!-- Div only shows if Header is true (1) -->
        <h5>{{ item.Text }}</h5>
      </div>
      <div v-else-if="item.Text === '[emptyRow]'">&nbsp;</div>
      <div v-else>
        <!-- Div only shows if Header is false (0) -->
        <div>{{ item.Text }}</div>
        <small v-if="item.Item"><subLink :linkitem="item.Item" /></small>
      </div>
    </div>
  </b-col>
</template>
<script>
export default {
  props: ['propItems'],
  data: function () {
    return {
      Items: this.propItems
    };
  },
};
</script>
