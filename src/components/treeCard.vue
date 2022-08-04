<script setup>
const dataList = [
    '集团总部党委',
    '联华股份党委',
    '百联股份党委',
    '物贸股份党委',
    '第一医药党委',
    '全渠道党委',
    '商投公司党总支',
    '百联金服党总支',
    '财务公司党支部',
    '现代物流党委',
    '百联置业党委',
    '百联资控党支部',
    '百联资产党委',
    '三联公司党委',
    '教培中心党委',
    '人力中心党委',
    '机关离退休党委'
]

const data = [{
    id: 'root',
    label: '集团党委',
    children: dataList.map((item, index) => {
        return {
            id: index,
            label: item,
            children: Array.from({ length: 10 }).fill({ label: 'label' }),
        }
    })
}]
const props = {
    value: 'id',
    label: 'label',
    children: 'children',
}

const filterText = ref('')
const treeRef = ref()
const refreshkey = ref(0)

watch(filterText, (val) => {
    treeRef.value.filter(val)
})

const filterNode = (value, data) => {
    if (!value) return ++refreshkey.value
    return data.label.includes(value)
}
</script>
<template>
    <el-card>
        <el-input v-model="filterText"
                  placeholder="请输入组织名称" />
        <el-tree ref="treeRef"
                 :key="refreshkey"
                 :data="data"
                 :props="props"
                 node-key="id"
                 :current-node-key="'root'"
                 :default-expanded-keys="['root']"
                 highlight-current
                 :filter-node-method="filterNode"
                 accordion
                 style="height:700px;overflow:auto;" />

    </el-card>

</template>

<style lang="scss" scoped>
@import '@/assets/scrollStyle.css';

.el-card {
    flex-basis: 300px;

    .el-input {
        margin-bottom: 20px;
    }

}
</style>
