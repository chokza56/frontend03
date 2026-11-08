<template>
    <div>
         <div class="min-h-screen flex items-center justify-center">
            <div class=" w-full max-w-md bg-white p-8 rounded-2xl shadow-xl">
                <h1 class="t-xl">สมัครสมาชิก</h1>
                <div>
                    <label class="text-gray-600">Name</label>
                    <input v-model="name" type="text" placeholder="Your Name" class="input-field" required/>

                    <label class="text-gray-600">Email</label>
                    <input v-model="email" type="email" placeholder="example@email.com" class="input-field" required/>

                    <label class="text-gray-600">Password</label>
                    <input v-model="password" type="password" placeholder="••••••••" class="input-field" required/>

                    <label class="text-gray-600">Phone</label>
                    <input v-model="phone" type="tel" placeholder="" class="input-field" required/>
                    
                    <label class="text-gray-600">salary</label>
                    <input v-model="salary" type="number" class="input-field" required/>

                    <label class="text-gray-600">Czid</label>
                    <input v-model="czid" type="tel" placeholder="" class="input-field" required/>

                    <label class="text-gray-600">Birthday</label>
                    <input v-model="birthday" type="date" class="input-field" required/>

                    <label class="text-gray-600">position</label>
                    <select v-model="position" class="input-field" required>
                        <option value="">ไม่มี</option>
                        <option value="admin">ผู้บริหาร</option>
                        <option value="user">ครู</option>
                    </select>

                    <label class="text-gray-600">department</label>
                    <select v-model="department" class="input-field" required>
                        <option value="">ไม่มี</option>
                        <option value="admin">เทคโนโลยีสารสนเทศ</option>
                        <option value="user">บัญชี</option>
                        <option value="user">การตลาด</option>
                    </select>

                    <label class="text-gray-600">status</label>
                    <select v-model="status" class="input-field" required>
                        <option value="">ไม่มี</option>
                        <option value="admin">ผู้รับการประเมิน</option>
                        <option value="user">กรรมการผู้ประเมิน</option>
                    </select>
                </div>
                <div><br>
                    <button @click="submit" class="btn-blue">ลงทะเบียน</button>
                </div>
                <NuxtLink to="/" class="text-blue-500 hover:underline">เข้าสู่ระบบ</NuxtLink>
            </div>
        </div>
        
    </div>
</template>

<script setup>

</script>

<style scoped>

</style>