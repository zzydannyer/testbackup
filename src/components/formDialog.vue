
<script setup>
import { ElMessageBox, ElMessage } from 'element-plus'
import 'element-plus/es/components/message/style/css'
import 'element-plus/es/components/message-box/style/css'
import { nextTick } from 'vue';

const dialogVisible = ref(false)

const handleOpen = () => {
    dialogVisible.value = true
}

defineExpose({ handleOpen })
defineProps({ formName: { type: String, default: '' }, elForm: { type: Object, default: {} } })

const handleClose = done => {
    ElMessageBox.confirm('确认关闭？')
        .then(() => {
            done()
        })
        .catch(() => {
            // catch error
        })
}

const handleSubmit = async (formEl) => {

    if (!formEl) return
    await formEl.validate((valid, fields) => {
        if (valid) {
            ElMessage({
                type: 'success',
                message: '保存成功',
            })
            return dialogVisible.value = false
        }


    })

}
</script>

<template>
    <el-dialog v-model="dialogVisible"
               width="60%"
               :before-close="handleClose">
        <template #header>
            <div class="card-header">
                <span>{{ formName }}</span>
            </div>
        </template>
        <slot name="content" />
        <template #footer>
            <span class="dialog-footer">
                <el-button type="danger"
                           plain
                           @click="dialogVisible = false">
                    <el-icon>
                        <CircleCloseFilled />
                    </el-icon>
                    取消
                </el-button>
                <el-button type="primary"
                           plain
                           @click="handleSubmit(elForm)">
                    <el-icon>
                        <CircleCheckFilled />
                    </el-icon>
                    保存
                </el-button>
            </span>
        </template>
    </el-dialog>
</template>
<style lang="scss" scoped>
.el-dialog {
    .card-header {
        display: flex;
    }

    .dialog-footer {
        display: flex;
        justify-content: center;

        .el-icon {
            margin-right: 5px
        }
    }
}
</style>

