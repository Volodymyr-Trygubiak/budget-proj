<template >
  <div class="list-item">
    <span class="budget-comment"
      >{{ item.comment }} <i :class="itemIcon"></i
    ></span>
    <span class="budget-value" :class="valueColor">{{ item.value }}</span>
    <ElButton type="danger" size="mini" @click="dialogVisible = true">
      Delete
    </ElButton>
    <ElDialog
      title="Do you want delete this value?"
      :visible.sync="dialogVisible"
    >
      <span class="value">{{ item.value }}</span>
      <span slot="footer" class="dialog-footer">
        <el-button
          type="primary"
          @click="
            deleteItem(item.id);
            dialogVisible = false;
          "
        >
          Confirm</el-button
        >
        <el-button @click="dialogVisible = false">Cancel</el-button>
      </span>
    </ElDialog>
  </div>
</template>

<script>
export default {
  name: "BudgetListItem",

  props: {
    item: {
      type: Object,
      default: () => ({}),
    },
  },

  data() {
    return {
      dialogVisible: false,
    };
  },

  computed: {
    itemIcon() {
      if (this.item.value > 0) {
        return "el-icon-top";
      } else if (this.item.value < 0) {
        return "el-icon-bottom";
      } else {
        return "";
      }
    },
    valueColor() {
      if (this.item.value > 0) {
        return "more";
      }
      if (this.item.value < 0) {
        return "less";
      } else {
        return "";
      }
    },
  },

  methods: {
    deleteItem(id) {
      this.$emit("delete-item", id);
    },
  },
};
</script>

<style scoped>
.list-item {
  display: flex;
  align-items: center;
  padding: 10px 15px;
}
.budget-value {
  font-weight: bold;
  margin-left: auto;
  margin-right: 20px;
}
.value {
  font-size: 28px;
}
.confirm {
  display: block;
  width: 400px;
  height: 300px;
}
</style>