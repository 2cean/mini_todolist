<script setup lang="ts">
import { Head, Link, useForm } from '@inertiajs/vue3';

// 로그인 데이터 초기화
const form = useForm({
    email: '',
    password: '',
    remember: false,
});

// 로그인 요청
const submit = () => {
    form.post(route('login'), {
        onFinish: () => {
            form.reset('password');
        },
    });
};
</script>

<template>
    <div class="flex min-h-screen items-center justify-center bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500">
        <div class="bg-white p-8 rounded-2xl shadow-lg w-full max-w-md">
            <Head title="로그인" />

            <h2 class="text-2xl font-bold text-gray-800 text-center">로그인</h2>
            <p class="text-sm text-gray-700 text-center mb-6">계정 정보를 입력하세요</p>

            <!-- 상태 메시지 -->
            <div v-if="status" class="mb-4 text-sm font-medium text-green-400">
                {{ status }}
            </div>

            <form @submit.prevent="submit">
                <!-- 이메일 입력 -->
                <div>
                    <label for="email" class="block text-sm font-medium text-gray-700">이메일</label>
                    <input
                        id="email"
                        type="email"
                        v-model="form.email"
                        required
                        class="mt-1 w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500"
                        autocomplete="username"
                    />
                    <p v-if="form.errors.email" class="text-red-500 text-xs mt-1">{{ form.errors.email }}</p>
                </div>

                <!-- 비밀번호 입력 -->
                <div class="mt-4">
                    <label for="password" class="block text-sm font-medium text-gray-700">비밀번호</label>
                    <input
                        id="password"
                        type="password"
                        v-model="form.password"
                        required
                        class="mt-1 w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500"
                        autocomplete="current-password"
                    />
                    <p v-if="form.errors.password" class="text-red-500 text-xs mt-1">{{ form.errors.password }}</p>
                </div>

                <!-- 로그인 유지 체크박스 -->
                <div class="mt-4 flex items-center">
                    <input
                        type="checkbox"
                        id="remember"
                        v-model="form.remember"
                        class="h-4 w-4 border border-gray-400 bg-purple-10 rounded focus:ring-indigo-400 checked:bg-indigo-500 checked:border-transparent transition duration-300 ease-in-out"
                    />
                    <label for="remember" class="ml-2 text-sm text-gray-700"> 로그인 유지하기 </label>
                </div>

                <!-- 로그인 버튼 -->
                <button
                    type="submit"
                    class="mt-6 w-full bg-indigo-500 hover:bg-indigo-600 text-white py-2 rounded-lg text-lg font-semibold shadow-md transition duration-300 ease-in-out"
                    :disabled="form.processing"
                >
                    로그인
                </button>
            </form>

            <!-- 비밀번호 찾기 & 회원가입 -->
            <div class="mt-4 text-center">
                <Link
                    v-if="canResetPassword"
                    :href="route('password.request')"
                    class="text-sm text-gray-700 hover:text-gray-200"
                >
                    비밀번호를 잊으셨나요?
                </Link>
                <p class="text-sm text-gray-700 mt-2">
                    계정이 없으신가요?
                    <Link :href="route('register')" class="text-indigo-400 hover:text-indigo-300">회원가입</Link>
                </p>
            </div>
        </div>
    </div>
</template>
