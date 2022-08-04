<script setup>
const childComp = ref()
const formEl = ref()
const formName = ref('新增党员')
const handleClick = () => {
    childComp.value.handleOpen()
}

const form = reactive({
    name: '',
    birthday: ''
})
const formRules = reactive({
    name: [{ required: true, message: '请输入姓名', trigger: 'blur' }],
    birthday: [{ required: true, message: '请输入生日日期', trigger: 'blur' }]
})



</script>

<template>
    <el-card :body-style="{ display: 'flex', justifyContent: 'flex-start' }">
        <el-button type="primary"
                   plain
                   @click="handleClick">新增</el-button>
    </el-card>

    <form-dialog ref="childComp"
                 :formName="formName"
                 :elForm="formEl">
        <template #content>
            <el-form ref="formEl"
                     :model="form"
                     :rules="formRules">
                <el-row>
                    <el-col :span="12">
                        <el-form-item label="姓名" prop="name">
                            <el-input v-model="form.name"
                                      autocomplete="off" />
                        </el-form-item>
                        <el-form-item label="出生日期" prop="birthday">
                            <el-date-picker v-model="form.birthday"
                                            type="date"
                                            format="YYYY年MM月DD"
                                            placeholder="请选择日期" />
                        </el-form-item>
                    </el-col>
                    <el-col :span="12">
                        <div class="grid-content ep-bg-purple-light" />
                    </el-col>
                </el-row>
            </el-form>

        </template>
    </form-dialog>

</template>
<style scoped>
.el-card {
    flex: 1;
    margin-left: 20px;

}
</style>