<script setup lang="ts">
import { Head, Link, useForm } from '@inertiajs/vue3';

// 회원가입 데이터 초기화
const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

// 회원가입 제출
const submit = () => {
    form.post(route('register'), {
        onFinish: () => {
            form.reset('password', 'password_confirmation');
        },
    });
};
</script>

<template>
    <div class="flex min-h-screen items-center justify-center bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500">
        <div class="bg-white p-8 rounded-2xl shadow-lg w-full max-w-md">
            <Head title="회원가입" />

            <h2 class="text-2xl font-bold text-gray-800 text-center">회원가입</h2>
            <p class="text-sm text-gray-500 text-center mb-6">빠르게 가입하고 시작하세요!</p>

            <form @submit.prevent="submit">
                <!-- 이름 입력 -->
                <div>
                    <label for="name" class="block text-sm font-medium text-gray-700">이름</label>
                    <input
                        id="name"
                        type="text"
                        v-model="form.name"
                        required
                        class="mt-1 w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500"
                        autocomplete="name"
                    />
                    <p v-if="form.errors.name" class="text-red-500 text-xs mt-1">{{ form.errors.name }}</p>
                </div>

                <!-- 이메일 입력 -->
                <div class="mt-4">
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
                        autocomplete="new-password"
                    />
                    <p v-if="form.errors.password" class="text-red-500 text-xs mt-1">{{ form.errors.password }}</p>
                </div>

                <!-- 비밀번호 확인 -->
                <div class="mt-4">
                    <label for="password_confirmation" class="block text-sm font-medium text-gray-700">비밀번호 확인</label>
                    <input
                        id="password_confirmation"
                        type="password"
                        v-model="form.password_confirmation"
                        required
                        class="mt-1 w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500"
                        autocomplete="new-password"
                    />
                    <p v-if="form.errors.password_confirmation" class="text-red-500 text-xs mt-1">
                        {{ form.errors.password_confirmation }}
                    </p>
                </div>

                <!-- 회원가입 버튼 -->
                <button
                    type="submit"
                    class="mt-6 w-full bg-indigo-500 hover:bg-indigo-600 text-white py-2 rounded-lg text-lg font-semibold shadow-md transition duration-300 ease-in-out"
                    :disabled="form.processing"
                >
                    회원가입
                </button>
            </form>

            <!-- 로그인 링크 -->
            <p class="mt-4 text-center text-sm text-gray-600">
                이미 계정이 있으신가요?
                <Link :href="route('login')" class="text-indigo-400 hover:text-indigo-300">로그인</Link>
            </p>
        </div>
    </div>
</template>
