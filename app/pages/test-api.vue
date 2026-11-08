<template>
    <div>
        <div>
            <div>
                <label>ชื่อ:</label>
                <input v-model="name" type="text" />
            </div>
            <div>
                <label>อีเมล:</label>
                <input v-model="email" type="email" />
            </div>
            <div>
                <label>อายุ:</label>
                <input v-model.number   ="age" type="number" />
            </div>
        </div>
        <div>
            <button @click="addstudent" :disabled="loading">
                {{ loading ? 'กำลังบันทึก...' : 'บันทึกข้อมูล' }}
            </button>
        </div>   
    </div>  
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const name = ref('')
const email = ref('')
const age = ref('')

const loading = ref(false)

const addstudent = async ( ) => {
    if (!name.value || !email.value || !age.value) {
        alert('กรุณากรอกข้อมูลให้ครบถ้วน')
        return
    }

    if (loading.value) return

    try {

        loading.value = true
        
        const response = await axios.post(
            'https://jsonplaceholder.typicode.com/posts',
            {
                name: name.value,
                email: email.value,
                age: age.value
            }
        )

        console.log(response.data)
        alert('บันทึกข้อมูลเรียบร้อยแล้ว')

    } catch (error) {
        console.error(error)
        alert('เกิดข้อผิดพลาด')
    } finally {
        loading.value = false
    }
}
</script>

<style lang="scss" scoped>

</style>