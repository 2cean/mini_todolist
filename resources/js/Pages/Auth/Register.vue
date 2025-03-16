<template>
    <div class="register-container">
        <div class="card">
            <div class="card-body">
                <h2 class="text-center">회원가입</h2>
                <form @submit.prevent="handleRegister">
                    <div class="mb-3">
                        <label class="form-label">이름</label>
                        <input type="text" v-model="name" class="form-control" placeholder="이름 입력" required />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">이메일</label>
                        <input type="email" v-model="email" class="form-control" placeholder="이메일 입력" required />
                    </div>
                    <div class="mb-3">
                        <label class="form-label">비밀번호</label>
                        <input type="password" v-model="password" class="form-control" placeholder="비밀번호 입력" required />
                    </div>
                    <button type="submit" class="btn btn-success w-100">가입하기</button>
                </form>
                <p class="text-center mt-3">
                    이미 계정이 있으신가요?
                    <Link :href="route('login')">
                        로그인
                    </Link>
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import login from "@/Pages/Auth/Login.vue";
import {Link} from "@inertiajs/vue3";

export default {
    components: {Link},
    computed: {
        login() {
            return login
        }
    },
    data() {
        return {
            name: "",
            email: "",
            password: ""
        };
    },
    methods: {
        async handleRegister() {
            try {
                const response = await axios.post("http://127.0.0.1:8000/register", {
                    name: this.name,
                    email: this.email,
                    password: this.password
                });
                alert("회원가입 성공! 🎉 로그인 페이지로 이동합니다.");
                this.$router.push("/login");
            } catch (error) {
                console.error(error);
                alert("회원가입 실패! 😭 다시 시도해주세요.");
            }
        }
    }
};
</script>

<style scoped>
.register-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(to right, #eef2f3, #d7dde8);
}

.card {
    width: 100%;
    max-width: 400px;
    padding: 20px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
}
</style>
