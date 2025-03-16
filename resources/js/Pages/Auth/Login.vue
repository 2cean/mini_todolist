<template xmlns:Link="http://www.w3.org/1999/html">
    <div class="login-container">
        <div class="card">
            <div class="card-body">
                <h2 class="text-center">로그인</h2>
                <form @submit.prevent="handleLogin">
                    <div class="mb-3">
                        <label for="email" class="form-label">이메일</label>
                        <input type="email" v-model="email" class="form-control" placeholder="이메일 입력" required />
                    </div>
                    <div class="mb-3">
                        <label for="password" class="form-label">비밀번호</label>
                        <input type="password" v-model="password" class="form-control" placeholder="비밀번호 입력" required />
                    </div>
                    <button type="submit" class="btn btn-primary w-100">로그인</button>
                </form>
                <p class="text-center mt-3">
                    계정이 없으신가요?
                    <Link :href="route('register')">
                        회원가입하기
                    </Link>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import {Link} from "@inertiajs/vue3";

export default {
    components: {Link},
    data() {
        return {
            email: "",
            password: ""
        };
    },
    methods: {
        handleLogin() {
            alert(`로그인 시도: ${this.email}`);
            // 여기서 실제 로그인 API 호출하면 됨
        }
    }
};
</script>

<style scoped>
/* 배경 스타일 */
.login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(to right, #eef2f3, #d7dde8);
}

/* 카드 스타일 */
.card {
    width: 100%;
    max-width: 400px;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
}
</style>
