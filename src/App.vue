<template>
  <div class="select-tree-box">
    <div @click="addExpand">add, 当前展开值为{{expandedKeys}}</div>

    <div class="treeBox">
      <a-tree-select
        v-model="checkedKeys"
        style="width: 100%"
        :tree-data="treeData"
        tree-checkable
        :show-checked-strategy="SHOW_PARENT"
        search-placeholder="Please select"
        :replace-fields="replaceFields"
        :open="visibleOpen"
        :treeExpandedKeys="expandedKeys"
        :get-popup-container="target => target.parentNode"
      />
     
    </div>
  </div>
</template>
<script>
import { TreeSelect } from 'ant-design-vue';
const SHOW_PARENT = TreeSelect.SHOW_PARENT;

export default {
  name: 'TestTree',
  data () {
    return {
      checkedKeys: [],
      expandedKeys: [],
      treeData: [{"id":5001,"name":"测试1（ID：5001）","child":[{"id":7367,"name":"测试2（ID：7367）","child":[],},],}],
      SHOW_PARENT,
      replaceFields: {
        children: 'child',
        title: 'name',
        key: 'id',
        label: 'name',
        value: 'id',
      },
      fetching: false,
      visibleOpen: true,
    };
  },
  methods: {
    addExpand () {
      this.expandedKeys.push(7367)
    }
  },
};
</script>
