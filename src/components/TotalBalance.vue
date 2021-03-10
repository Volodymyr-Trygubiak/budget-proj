<template>
  <div class="total-value" :class="totalColor">Balance: {{ total }}</div>
</template>

<script>
export default {
  name: "TotalBalance",
  props: {
    total: {
      type: Number,
      default: 0,
    },
  },

  computed: {
    totalColor() {
      if (this.total > 0) {
        return "more";
      }if (this.total < 0) {
        return "less";
      } else {
        return '';
      }
    },
  },
};
</script>

<style scoped>
.total-value {
  font-size: 26px;
  text-transform: uppercase;
  padding: 20px;
  text-align: center;
}
.more {
  color: #1cca47;
}
.less {
  color: #ff0000;
}
</style>