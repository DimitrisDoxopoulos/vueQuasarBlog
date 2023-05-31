<template>
  <q-page>
    <div class="row">
      <div class="col-12 col-md-4 col-lg-4 q-pa-xl">
        <div class="text-center">
          <q-img src="~/src/assets/logo.jpg" class="logo"/>
        </div>
        <div class="text-h4 text-bold q-mt-lg text-indigo">View Moto</div>
        <div class="text-gray-7">Please log in your account below</div>
        <div class="column q-mt-sm">
          <q-input
            outlined v-model="form.email.value"
            :error="form.email.error"
            :error-message="form.email.msg"
            label="Enter Email *"
            @update:model-value="validateInput(form, 'email')"
            @blur="validateInput(form, 'email')"
          >
            <template v-slot:prepend>
              <q-icon name="email"></q-icon>
            </template>
          </q-input>
          <q-input
            class="q-mt-sm"
            outlined
            v-model="form.password.value"
            :error="form.password.error"
            :error-message="form.password.msg"
            label="Enter Password *"
            @update:model-value="validateInput(form, 'password')"
            @blur="validateInput(form, 'password')"
          >
            <template v-slot:prepend>
              <q-icon name="lock" />
            </template>
            <template v-slot:append>
              <q-icon
                @click="isPassword = !isPassword"
                :name="isPassword ? 'visibility_off' : 'visibility'"
              />
            </template>
          </q-input>
        </div>
        <div class="q-mt-sm text-left">
          <q-btn
            flat
            no-caps
            color="indigo"
          >
            Forgot Password
          </q-btn>
        </div>
        <div class="column q-mt-sm">
          <q-btn
            @click="submitLogin"
            :disable="!isSubmitBtn(form)"
            :color= "!isSubmitBtn(form) ? 'gray-6' : 'indigo'"
          >
            Login
          </q-btn>
        </div>
        <div class="text-gray-7 text q-mt-lg">Log in with Social Media</div>
        <div class="text-center q-mt=md">
          <q-btn size="lg" class="q-ma-xs" color="red" icon="mail" />
          <q-btn size="lg" class="q-ma-xs" color="primary" icon="facebook" />
        </div>
      </div>
      <div class="col-12 col-md-8 col-lg-8 text-center">
        <q-img class="login-logo" src="~/src/assets/main-login-image.jpg" />
      </div>
    </div>
  </q-page>
</template>

<script setup>
import Hooks from 'src/hooks'
import { ref } from 'vue'

const { isFormValid, validateInput, isSubmitBtn } = Hooks()
const isPassword = ref(true)
const form = ref({
  email: {
    value: '',
    email: true,
    requiredMsg: 'Email is required',
    emailMsg: 'Invalid email address',
    required: true
  },
  password: {
    value: '',
    requiredMsg: 'Password is required',
    required: true
  }
})

const submitLogin = () => {
  if (!isFormValid) return false
}
</script>
<style scoped>
  .logo {
    widows: 50%;
  }
  .login-logo {
    width: 70%;
    margin-top: 10px;
  }
</style>
