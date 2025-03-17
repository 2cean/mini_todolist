<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';

defineProps<{
    canLogin?: boolean;
    canRegister?: boolean;
}>();

function handleImageError() {
    document.getElementById('screenshot-container')?.classList.add('!hidden');
    document.getElementById('docs-card')?.classList.add('!row-span-1');
    document.getElementById('docs-card-content')?.classList.add('!flex-row');
    document.getElementById('background')?.classList.add('!hidden');
}
</script>

<template>
    <Head title="Welcome" />
    <div class="flex min-h-screen items-center justify-center bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500">
        <div
            class="relative flex min-h-screen flex-col items-center justify-center selection:bg-[#FF2D20] selection:text-white"
        >
            <div class="relative w-full max-w-2xl px-6 lg:max-w-7xl">
                <header
                    class="grid grid-cols-2 items-center gap-2 py-10 lg:grid-cols-3"
                >
                    <div class="flex lg:col-start-2 lg:justify-center">
                        <svg
                            class="h-12 w-auto lg:h-16 justify-content-center transition mt-1 lg:text-white"
                            viewBox="0 0 17 16"
                            fill="white"
                            xmlns="http://www.w3.org/2000/svg"
                        >
                            <path d="M3 2.5C3 2.22386 3.22386 2 3.5 2H9.08579C9.21839 2 9.34557 2.05268 9.43934 2.14645L11.8536 4.56066C11.9473 4.65443 12 4.78161 12 4.91421V12.5C12 12.7761 11.7761 13 11.5 13H3.5C3.22386 13 3 12.7761 3 12.5V2.5ZM3.5 1C2.67157 1 2 1.67157 2 2.5V12.5C2 13.3284 2.67157 14 3.5 14H11.5C12.3284 14 13 13.3284 13 12.5V4.91421C13 4.51639 12.842 4.13486 12.5607 3.85355L10.1464 1.43934C9.86514 1.15804 9.48361 1 9.08579 1H3.5ZM4.5 4C4.22386 4 4 4.22386 4 4.5C4 4.77614 4.22386 5 4.5 5H7.5C7.77614 5 8 4.77614 8 4.5C8 4.22386 7.77614 4 7.5 4H4.5ZM4.5 7C4.22386 7 4 7.22386 4 7.5C4 7.77614 4.22386 8 4.5 8H10.5C10.7761 8 11 7.77614 11 7.5C11 7.22386 10.7761 7 10.5 7H4.5ZM4.5 10C4.22386 10 4 10.2239 4 10.5C4 10.7761 4.22386 11 4.5 11H10.5C10.7761 11 11 10.7761 11 10.5C11 10.2239 10.7761 10 10.5 10H4.5Z"
                                  fill="white"
                            ></path>
                        </svg>
                        <h1 class="rounded-md py-2  ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-amber-400 dark:hover:text-white dark:focus-visible:ring-white"
                        >
                            <strong>
                                Todo Challenges
                            </strong>
                        </h1>
                    </div>


<!--                    네비게이션 필요시 주석 해제-->


<!--                    <nav v-if="canLogin" class="-mx-3 flex flex-1 justify-end">-->
<!--                        <Link-->
<!--                            v-if="$page.props.auth.user"-->
<!--                            :href="route('dashboard')"-->
<!--                            class="rounded-md px-3 py-2 dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"-->
<!--                        >-->
<!--                            메인페이지-->
<!--                        </Link>-->

<!--                        <template v-else>-->
<!--                            <Link-->
<!--                                :href="route('login')"-->
<!--                                class="rounded-md px-3 py-2 dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"-->
<!--                            >-->
<!--                                로그인-->
<!--                            </Link>-->

<!--                            <Link-->
<!--                                v-if="canRegister"-->
<!--                                :href="route('register')"-->
<!--                                class="rounded-md px-3 py-2 dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"-->
<!--                            >-->
<!--                                회원가입-->
<!--                            </Link>-->
<!--                        </template>-->
<!--                    </nav>-->


                </header>

                <main class="mt-6">
                    <div class="grid gap-6 lg:grid-cols-2 lg:gap-8">
                        <div
                            id="docs-card"
                            class="flex flex-col items-start gap-6 overflow-hidden rounded-lg  p-6 shadow-lg ring-1 bg-white/30 backdrop-blur-md md:row-span-3 lg:p-10 lg:pb-10"
                        >
                            <div
                                id="screenshot-container"
                                class="relative flex w-full flex-1 items-stretch "
                            >
                                <img
                                    src="https://laravel.com/assets/img/welcome/docs-light.svg"
                                    alt="Laravel documentation screenshot"
                                    class="aspect-video h-full w-full flex-1 rounded-[10px] object-cover object-top drop-shadow-[0px_4px_34px_rgba(0,0,0,0.06)] dark:hidden"
                                    @error="handleImageError"
                                />
                                <img
                                    src="https://laravel.com/assets/img/welcome/docs-dark.svg"
                                    alt="Laravel documentation screenshot"
                                    class="hidden aspect-video h-full w-full flex-1 rounded-[10px] object-cover object-top drop-shadow-[0px_4px_34px_rgba(0,0,0,0.25)] dark:block"
                                />
                            </div>

                            <div
                                class="relative flex items-center gap-6 lg:items-end"
                            >
                                <div
                                    id="docs-card-content"
                                    class="flex items-start gap-6 lg:flex-col"
                                >
                                    <div
                                        class="flex size-12 shrink-0 items-center justify-center rounded-full bg-[#FF2D20]/10 sm:size-16 hover:bg-white/10"
                                    >
                                        <svg
                                            class="size-5 sm:size-6"
                                            xmlns="http://www.w3.org/2000/svg"
                                            fill="none"
                                            viewBox="0 0 24 24"
                                        >
                                            <path
                                                fill="#FF2D20"
                                                d="M23 4a1 1 0 0 0-1.447-.894L12.224 7.77a.5.5 0 0 1-.448 0L2.447 3.106A1 1 0 0 0 1 4v13.382a1.99 1.99 0 0 0 1.105 1.79l9.448 4.728c.14.065.293.1.447.1.154-.005.306-.04.447-.105l9.453-4.724a1.99 1.99 0 0 0 1.1-1.789V4ZM3 6.023a.25.25 0 0 1 .362-.223l7.5 3.75a.251.251 0 0 1 .138.223v11.2a.25.25 0 0 1-.362.224l-7.5-3.75a.25.25 0 0 1-.138-.22V6.023Zm18 11.2a.25.25 0 0 1-.138.224l-7.5 3.75a.249.249 0 0 1-.329-.099.249.249 0 0 1-.033-.12V9.772a.251.251 0 0 1 .138-.224l7.5-3.75a.25.25 0 0 1 .362.224v11.2Z"
                                            />
                                            <path
                                                fill="#FF2D20"
                                                d="m3.55 1.893 8 4.048a1.008 1.008 0 0 0 .9 0l8-4.048a1 1 0 0 0-.9-1.785l-7.322 3.706a.506.506 0 0 1-.452 0L4.454.108a1 1 0 0 0-.9 1.785H3.55Z"
                                            />
                                        </svg>
                                    </div>

                                    <div class="pt-3 sm:pt-5 lg:pt-0">
                                        <h2
                                            class="text-xl font-semibold text-white"
                                        >
                                            Laravel & Vue 미니 프로젝트
                                        </h2>

                                        <p class="mt-4 text-sm/relaxed text-amber-400 ">
                                            <strong>
                                                Laravel & Vue 를 사용하여 웹페이지를 구축하는 실습용 프로젝트<br>
                                                todo를 등록하고 조회,수정,삭제가 가능하며, 여러개의 todo를 도전하는
                                                challenge 기능을 추가하여 유저간 소통도 가능하고 동기부여에 도움이 되는
                                                웹 어플리케이션을 만들고자 했습니다
                                            </strong>
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <a
                            href="/register"
                            class="flex items-start gap-4 rounded-lg p-6 bg-white/30 backdrop-blur-md shadow-lg hover:bg-white/10 lg:pb-10 text-decoration-none"
                        >
                            <div
                                class="flex size-12 shrink-0 items-center justify-center rounded-full bg-[#FF2D20]/10 sm:size-16 hover:bg-white/10"
                            >
                                <svg
                                    class="size-5 sm:size-6 stroke-[#FF2D20]"
                                    viewBox="0 0 15 15"
                                    fill="none"
                                    xmlns="http://www.w3.org/2000/svg"
                                >
                                    <g fill="#FF2D20">
                                        <path
                                            d="M8 2.75C8 2.47386 7.77614 2.25 7.5 2.25C7.22386 2.25 7 2.47386 7 2.75V7H2.75C2.47386 7 2.25 7.22386 2.25 7.5C2.25 7.77614 2.47386 8 2.75 8H7V12.25C7 12.5261 7.22386 12.75 7.5 12.75C7.77614 12.75 8 12.5261 8 12.25V8H12.25C12.5261 8 12.75 7.77614 12.75 7.5C12.75 7.22386 12.5261 7 12.25 7H8V2.75Z"
                                        />
                                    </g>
                                </svg>
                            </div>

                            <div class="pt-3 sm:pt-5">
                                <h2
                                    class="text-xl font-semibold text-white"
                                >
                                    회원가입 하기
                                </h2>

                                <p class="mt-4 text-sm/relaxed text-amber-400">
                                    <strong>
                                        Todo Challenges에 오신것을 환영합니다!<br>
                                        가장 먼저 회원가입을 진행하여 주세요! 할일 체크리스트(todo)를 등록하고 관리할 수 있습니다
                                    </strong>
                                </p>
                            </div>

                            <svg
                                class="size-6 shrink-0 self-center stroke-[#FF2D20]"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="none"
                                viewBox="0 0 24 24"
                                stroke-width="1.5"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75"
                                />
                            </svg>
                        </a>

                        <a
                            href="/login"
                            class="flex items-start gap-4 rounded-lg p-6 bg-white/30 backdrop-blur-md shadow-lg hover:bg-white/10 lg:pb-10 text-decoration-none"
                        >
                            <div
                                class="flex size-12 shrink-0 items-center justify-center rounded-full bg-[#FF2D20]/10 sm:size-16"
                            >
                                <svg
                                    class="size-5 sm:size-6 stroke-[#FF2D20]"
                                    viewBox="0 0 15 15"
                                    fill="none"
                                    xmlns="http://www.w3.org/2000/svg"
                                >
                                    <g fill="#FF2D20">
                                        <path
                                            d="M4.5 1C4.22386 1 4 1.22386 4 1.5C4 1.77614 4.22386 2 4.5 2H12V13H4.5C4.22386 13 4 13.2239 4 13.5C4 13.7761 4.22386 14 4.5 14H12C12.5523 14 13 13.5523 13 13V2C13 1.44772 12.5523 1 12 1H4.5ZM6.60355 4.89645C6.40829 4.70118 6.09171 4.70118 5.89645 4.89645C5.70118 5.09171 5.70118 5.40829 5.89645 5.60355L7.29289 7H0.5C0.223858 7 0 7.22386 0 7.5C0 7.77614 0.223858 8 0.5 8H7.29289L5.89645 9.39645C5.70118 9.59171 5.70118 9.90829 5.89645 10.1036C6.09171 10.2988 6.40829 10.2988 6.60355 10.1036L8.85355 7.85355C9.04882 7.65829 9.04882 7.34171 8.85355 7.14645L6.60355 4.89645Z" fill="currentColor" fill-rule="evenodd" clip-rule="evenodd"
                                        />
                                    </g>
                                </svg>
                            </div>

                            <div class="pt-3 sm:pt-5">
                                <h2
                                    class="text-xl font-semibold dark:text-white"
                                >
                                    로그인 하기
                                </h2>

                                <p class="mt-4 text-sm/relaxed text-amber-400">
                                    사용자들과 함께 다양한 chellenges에 도전해 보세요!<br>
                                    내가 직접 chellenge를 등록할 수도 있고, 참여한 사용자끼리 이야기를 나눌 수도 있습니다
                                </p>
                            </div>

                            <svg
                                class="size-6 shrink-0 self-center stroke-[#FF2D20]"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="none"
                                viewBox="0 0 24 24"
                                stroke-width="1.5"
                            >
                                <path
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75"
                                />
                            </svg>
                        </a>

                        <div
                            class="flex items-start gap-4 rounded-lg p-6 bg-white/30 backdrop-blur-md shadow-lg  lg:pb-10 text-decoration-none"
                        >
                            <div
                                class="flex size-12 shrink-0 items-center justify-center rounded-full bg-[#FF2D20]/10 sm:size-16"
                            >
                                <svg
                                    class="size-5 sm:size-6 stroke-[#FF2D20]"
                                    viewBox="0 0 15 15"
                                    fill="none"
                                    xmlns="http://www.w3.org/2000/svg"
                                >
                                    <g fill="#FF2D20">
                                        <path
                                            d="M11.4669 3.72684C11.7558 3.91574 11.8369 4.30308 11.648 4.59198L7.39799 11.092C7.29783 11.2452 7.13556 11.3467 6.95402 11.3699C6.77247 11.3931 6.58989 11.3355 6.45446 11.2124L3.70446 8.71241C3.44905 8.48022 3.43023 8.08494 3.66242 7.82953C3.89461 7.57412 4.28989 7.55529 4.5453 7.78749L6.75292 9.79441L10.6018 3.90792C10.7907 3.61902 11.178 3.53795 11.4669 3.72684Z" fill="currentColor" fill-rule="evenodd" clip-rule="evenodd"
                                        />
                                    </g>
                                </svg>
                            </div>

                            <div class="pt-3 sm:pt-5">
                                <h2
                                    class="text-xl font-semibold dark:text-white"
                                >
                                    모든 준비가 끝났습니다!
                                </h2>

                                <p class="mt-4 text-sm/relaxed dark:text-amber-400">
                                    직접 나만의 todo(할일목록)을 만들어보세요!<br>
                                    다른 사용자들이 등록한 challenge에 도전해보세요!
                                </p>
                            </div>
                        </div>
                    </div>
                </main>

                <footer
                    class="py-16 text-center text-sm dark:text-white/70"
                >
                    Todo Challenges
                </footer>
            </div>
        </div>
    </div>
</template>
