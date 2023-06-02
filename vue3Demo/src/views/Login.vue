<template>
   <el-form
    ref="ruleFormRef"
    :model="loginForm"
    status-icon
    :rules="rules"
    label-width="120px"
    class="demo-ruleForm"
  >
    <el-form-item label="Password" prop="pass">
      <el-input v-model="loginForm.pass" type="password" autocomplete="off" />
    </el-form-item>
    <el-form-item label="Confirm" prop="checkPass">
      <el-input
        v-model="ruleForm.checkPass"
        type="password"
        autocomplete="off"
      />
    </el-form-item>
    <el-form-item label="Age" prop="age">
      <el-input v-model.number="loginForm.age" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm(ruleFormRef)"
        >Submit</el-button
      >
      <el-button @click="resetForm(ruleFormRef)">Reset</el-button>
    </el-form-item>
  </el-form>
    
</template>
<script setup>

import {ref,reactive} from 'vue'
const ruleFormRef=ref(null)
const loginForm=reactive({
    pass:'',
    checkPass:'',
    name:''
})

const validateUserName = (rule, value, callback) => {
  if (value === '') {
    callback(new Error('Please input the name'))
  } else {
    if (loginForm.checkPass !== '') {
      if (!ruleFormRef.value) return
      ruleFormRef.value.validateField('name', () => null)
    }
    callback()
  }
}

const validatePass = (rule, value, callback) => {
  if (value === '') {
    callback(new Error('Please input the password'))
  } else {
    if (loginForm.checkPass !== '') {
      if (!ruleFormRef.value) return
      ruleFormRef.value.validateField('checkPass', () => null)
    }
    callback()
  }
}
const validatePass2 = (rule, value, callback) => {
  if (value === '') {
    callback(new Error('Please input the password again'))
  } else if (value !== loginForm.pass) {
    callback(new Error("Two inputs don't match!"))
  } else {
    callback()
  }
}


const rules = reactive({
  pass: [{ validator: validatePass, trigger: 'blur' }],
  checkPass: [{ validator: validatePass2, trigger: 'blur' }],
  name: [{ validator: validateUserName, trigger: 'blur' }],
})

const submitForm =(formEl)=>{
    if (!formEl) return
  formEl.validate((valid) => {
    if (valid) {
      console.log('submit!')
    } else {
      console.log('error submit!')
      return false
    }
  })

}

</script>

<style lang="scss" scoped>

.demo-ruleForm {
    width:500px;
    height: 500rpx;
    background:gray;
}


</style>