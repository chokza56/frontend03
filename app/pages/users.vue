
<script setup>
import { ref } from 'vue'
import axios from 'axios'

const name = ref('')
const studentid = ref('')

const result = ref(null)

const loading = ref(false)

const addStudent = async () => {

    if (loading.value) return

    try {
        loading.value = true

        const response = await axios.post(
            'https://jsonplaceholder.typicode.com/posts',
            {
                name: name.value,
                student_id: studentid.value
            }
        )

        console.log(response.data)
        alert('บันทึกข้อมูลเรียบร้อยแล้ว')
        result.value = response.data    

    } catch (error) {
        console.error(error)
        alert('เกิดข้อผิดพลาด')

    } finally {
        loading.value = false
    }
}
</script>

<template>
    <div>
        <h1>เพิ่มข้อมูลนักเรียน</h1>

        <input
            type="text"
            v-model="name"
            placeholder="ชื่อ"
        >

        <input
            type="number"
            v-model="studentid"
            placeholder="รหัสนักเรียน"
        >

        <div v-if="result"> 
            <h3>ข้อมูลที่บันทึก</h3>
            <p>ชื่อ: {{ result.name }}</p>
            <p>รหัสนักเรียน: {{ result.student_id }}</p>
            <p>ID จาก API: {{ result.id }}</p>
        </div>
        <button @click="addStudent" :disabled="loading">
            {{ loading ? 'กำลังบันทึก...' : 'บันทึกข้อมูล' }}
        </button>
    </div>
</template>
