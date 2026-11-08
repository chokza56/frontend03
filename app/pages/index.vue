<template>
    <div class="min-h-screen flex items-center justify-center bg-gray-100">

        <div class="w-full max-w-md bg-white p-8 rounded-2xl shadow-xl">

            <h1 class="t-xl">Login</h1>
            
            <label class="text-gray-600">UserName</label>
            <input class="input-field mb-3" type="text" v-model="name" placeholder="กรอกชื่อ...">

            <label class="text-gray-600">Password</label>
            <input class="input-field mb-3" type="password" v-model="pass" placeholder="กรอกรหัส...">

            <button @click="sub" class="btn-blue">เข้าสู่ระบบ</button>

        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'
import { useUserStore } from '~/stores/user'

const store = useUserStore()

const name = ref('')
const pass = ref('')

const sub = async () => {

    if (!name.value || !pass.value) {
        alert('กรอกให้ครบ')
        return
    }

    try {
        const res = await axios.post('https://reqres.in/api/login', {
            email: name.value,
            password: pass.value
        })

        store.token = res.data.token

        console.log(store.token)
        console.log(res.data)

        alert('เข้าสู่ระบบสำเร็จ')

        await navigateTo('/user/dashboard')

    } catch (err) {
        console.log(err.response?.data)
        alert('เข้าสู่ระบบไม่สำเร็จ')
    }
}
</script>
