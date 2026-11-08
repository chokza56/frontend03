<script setup>
import { ref ,onMounted , computed} from 'vue'
import axios from 'axios'

const students = ref([])

const searchText = ref('')

const filteredStudents = computed(() => {
    return students.value.filter(student => {
        return student.name.toLowerCase().includes(
            searchText.value.toLowerCase()
        )
    })
})


const getstudents = async () => {
    try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users')
        students.value = response.data
    } catch (error) {
        console.error(error)
        alert('เกิดข้อผิดพลาดในการดึงข้อมูลนักเรียน')
    }
}

onMounted(() => {
    getstudents()
})

</script>

<template>
    <div>
        <table>
            <thead>
                <tr>
                    <th>ชื่อ</th>
                    <th>อีเมล</th>
                    <th>โทรศัพท์</th>
                    <th>เว็บไซต์</th>
                </tr>
            </thead>
            <tbody>
                <tr      v-for="data in filteredStudents" :key="data.id">
                    <td>{{ data.name }}</td>
                    <td>{{ data.email }}</td>
                    <td>{{ data.phone }}</td>
                    <td>{{ data.website }}</td>
                </tr>
                 <tr v-if="filteredStudents.length === 0">
        <td colspan="4">ไม่พบข้อมูลนักเรียน</td>
    </tr>
            </tbody>    
        </table>

        <input type="text"
                placeholder="ค้นหาชื่อนักเรียน..."
                v-model="searchText">
    </div>
</template>