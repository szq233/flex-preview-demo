<script setup>
import { reactive, ref } from 'vue'
import {
  flexDirectionList,
  flexWrapList,
  justifyContentList,
  alignItemsList,
  alignContentList
} from '../constants/containerSelectOptions'
import {
  alignSelfList
} from '../constants/itemsSelectOptions'
const state = reactive({ count: 0 })
const count = ref(9)
const container = reactive({
  flexDirection: 'row',
  flexWrap: 'nowrap',
  justifyContent: 'flex-start',
  alignItems: 'stretch',
  alignContent: 'stretch',
})
const items = reactive({
  order: 0,
  flexGrow: 0,
  flexShrink: 1,
  flexBasis: 'auto',
  alignSelf: 'auto',
})
const checkbox = reactive({
 1: true
})

</script>

<template>
  <div class="hello-world">
    <div class="test-1">
      <div class="container" :style="{...container}">
        <div v-for="i in count" :key="i" contenteditable class="item" :style="checkbox[i] ? {...items} : {}">{{i}}</div>
      </div>
      <div class="actions">
        Flex容器（Flex Container）的相关配置项：
        <br/><br/>
        <el-form :model="container" label-width="120px" label-position="left">
          <el-form-item label="子项目数量:">
            <el-input-number v-model="count" :min="1" :max="99" />
          </el-form-item>
          <el-form-item label="flex-direction:">
            <el-select v-model="container.flexDirection">
              <el-option :label="t.label" :value="t.value" v-for="(t, i) in flexDirectionList" :key="i"/>
            </el-select>
          </el-form-item>
          <el-form-item label="flex-wrap:">
            <el-select v-model="container.flexWrap">
              <el-option :label="t.label" :value="t.value" v-for="(t, i) in flexWrapList" :key="i"/>
            </el-select>
          </el-form-item>
          <el-form-item label="justify-content:">
            <el-select v-model="container.justifyContent">
              <el-option :label="t.label" :value="t.value" v-for="(t, i) in justifyContentList" :key="i"/>
            </el-select>
          </el-form-item>
          <el-form-item label="align-items:">
            <el-select v-model="container.alignItems">
              <el-option :label="t.label" :value="t.value" v-for="(t, i) in alignItemsList" :key="i"/>
            </el-select>
          </el-form-item>
          <el-form-item label="align-content:">
            <el-select v-model="container.alignContent">
              <el-option :label="t.label" :value="t.value" v-for="(t, i) in alignContentList" :key="i"/>
            </el-select>
          </el-form-item>
        </el-form>
        <br/>
        Flex项目（Flex Items）的相关配置项：
        <br/><br/>
        <div>
          <el-checkbox v-model="checkbox[i]" :label="'item' + i" size="large" v-for="i in count" :key="i"/>
        </div>
        <br/>
        <el-form :model="items" label-width="120px" label-position="left">
          <el-form-item label="order:">
            <el-input v-model="items.order" placeholder="Please input" />
          </el-form-item>
          <el-form-item label="flex-grow:">
            <el-input v-model="items.flexGrow" placeholder="Please input" />
          </el-form-item>
          <el-form-item label="flex-shrink:">
            <el-input v-model="items.flexShrink" placeholder="Please input" />
          </el-form-item>
          <el-form-item label="flex-basis:">
            <el-input v-model="items.flexBasis" placeholder="Please input" />
          </el-form-item>
          <el-form-item label="align-self:">
            <el-select v-model="items.alignSelf">
              <el-option :label="t.label" :value="t.value" v-for="(t, i) in alignSelfList" :key="i"/>
            </el-select>
          </el-form-item>
        </el-form>
      </div>
    </div>
    <div class="test-2">

    </div>
  </div>
</template>

<style scoped lang="scss">
.test-1 {
  display: flex;
  .container {
    display: flex;
    width: 500px;
    border: 1px dashed #EB1D36;
    .item {
      // order: 2;
      width: 100px;
      height: 100px;
      background-color: #FF971D;
      box-sizing: border-box;
      border: 2px solid #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 10px;
    }
  }
  .actions {
    margin-left: 50px;
  }
}
</style>
