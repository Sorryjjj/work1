<template>
    <span class="text-large font-600 mr-3"> Transaction </span>
    <div class="form-wrapper">
        <el-form :model="formData" label-position="top" @submit.prevent="submitForm">
            <el-form-item :label="NAMESPACE_LABEL">
                <el-input v-model="formData.namespace_id" :placeholder="NAMESPACE_PLACEHOLDER" size="large"></el-input>
            </el-form-item>
            <el-form-item :label="HEX_ENCODED_LABEL">
                <el-input v-model="formData.data" :placeholder="HEX_ENCODED_PLACEHOLDER"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm" :loading="isLoading">{{ SUBMIT_BUTTON_TEXT }}</el-button>
            </el-form-item>
        </el-form>
    </div>
    <span class="text-large font-600 mr-3"> Result </span>
    <div v-if="result.value" class="form-wrapper">
        <TransactionResponse :jsonData="result.value"></TransactionResponse>
    </div>
    <div v-else>
        <el-empty description="No data" />
    </div>
</template>

<script setup>
import { ElForm, ElFormItem, ElInput, ElButton, ElEmpty } from 'element-plus'
import { HEX_ENCODED_PLACEHOLDER, NAMESPACE_PLACEHOLDER, NAMESPACE_LABEL, HEX_ENCODED_LABEL, SUBMIT_BUTTON_TEXT } from '@constants/index';
import useSendTransactions from "@hooks/useSendTransactions"
import TransactionResponse from './TransactionResponse.vue';
const { formData, submitForm, isLoading ,result} = useSendTransactions()

</script>

<style scoped>
.form-wrapper {
    width: 100%;
    margin-top: 10px;
}

</style>