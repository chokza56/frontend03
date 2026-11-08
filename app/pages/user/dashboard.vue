<template>
    <div class="min-h-screen bg-gray-100 p-8">

        <h1 class="text-2xl font-bold">Dashboard</h1>

        <p>เข้าสู่ระบบสำเร็จ</p>

        <p>Token: {{ store.token }}</p>

    </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user'

const store = useUserStore()
</script>