<template>
  <div class="budget-list-wrap">
    <ElCard :header="header">
      <el-button-group class="btn-group">
        <ElButton
          plain
          round
          type="success"
          size="mini"
          @click="returnIncome"
        >
          Income
        </ElButton>
        <ElButton
          plain
          round
          type="info"
          size="mini"
          @click="dialogVisible = true"
        >
          All
        </ElButton>
        <ElButton
          plain
          round
          type="danger"
          size="mini"
          @click="dialogVisible = true"
        >
          Outcome
        </ElButton>
      </el-button-group>
      <template v-if="!isEmpty">
        <BudgetListItem
          v-for="(item, prop) in list"
          :key="prop"
          :item="item"
          @delete-item="deleteItem"
        />
      </template>
      <ElAlert v-else type="info" :title="emptyTitle" :closable="false" />
    </ElCard>
  </div>
</template>

<script>
import BudgetListItem from "./BudgetListItem";
export default {
  name: "BudgetList",

  components: {
    BudgetListItem,
  },

  props: {
    list: {
      type: Object,
      default: () => ({}),
    },
  },

  data: () => ({
    header: "Budget List",
    emptyTitle: "Empty List",
  }),

  computed: {
    isEmpty() {
      return !Object.keys(this.list).length;
    },
  },

  methods: {
    deleteItem(id) {
      this.$emit("delete-item", id);
    },
    returnIncome() {
      console.log(Object.values(this.list)[1].type);
      console.log(Object.keys(this.list).length);

      for (let i = 0; i < this.list.length; i++)

      if (Object.values(this.list)[0].type === "INCOME") {
        return 
      }
      // for (let item in this.list) {
      //   if (item.type === "INCOME") {
      //     console.log(item);
      //   }
      // }
    }
  },
};
</script>

<style scoped>
.budget-list-wrap {
  max-width: 500px;
  margin: auto;
}
.btn-group {
  margin-bottom: 21px;
}
</style>