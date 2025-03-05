<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
</script>

<template>
    <Head title="KUWA Microfinance">
        <link rel="preconnect" href="https://rsms.me/" />
        <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
    </Head>
    <div class="flex min-h-screen flex-col items-center bg-[#F4F6F9] p-6 text-[#1b1b18] dark:bg-[#0a0a0a] lg:justify-center lg:p-8">
        <header class="mb-6 w-full max-w-[335px] text-sm lg:max-w-4xl">
            <nav class="flex items-center justify-end gap-4">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="inline-block rounded-sm border border-[#1b1b18] px-5 py-1.5 text-sm leading-normal text-[#1b1b18] hover:bg-[#004085] hover:text-white dark:border-[#EDEDEC] dark:text-[#EDEDEC] dark:hover:bg-[#62605b]"
                >
                    Dashboard
                </Link>
                <template v-else>
                    <Link
                        :href="route('login')"
                        class="inline-block rounded-sm border border-transparent px-5 py-1.5 text-sm leading-normal text-[#004085] hover:border-[#004085] hover:text-[#004085] dark:text-[#EDEDEC] dark:hover:border-[#EDEDEC]"
                    >
                        Log in
                    </Link>
                    <!-- <Link
                        :href="route('register')"
                        class="inline-block rounded-sm border border-[#004085] px-5 py-1.5 text-sm leading-normal text-[#004085] hover:bg-[#004085] hover:text-white dark:border-[#EDEDEC] dark:text-[#EDEDEC] dark:hover:bg-[#62605b]"
                    >
                        Register
                    </Link> -->
                </template>
            </nav>
        </header>
        <div class="duration-750 starting:opacity-0 flex w-full items-center justify-center opacity-100 transition-opacity lg:grow">
            <main class="flex w-full max-w-[335px] flex-col-reverse overflow-hidden rounded-lg lg:max-w-4xl lg:flex-row">
                <div
                    class="flex-1 rounded-bl-lg rounded-br-lg bg-white p-6 pb-12 text-[13px] leading-[20px] shadow-md dark:bg-[#161615] dark:text-[#EDEDEC] lg:rounded-br-none lg:rounded-tl-lg lg:p-20"
                >
                    <h1 class="mb-1 text-xl font-semibold text-[#004085]">Welcome to KUWA Microfinance</h1>
                    <p class="mb-4 text-[#706f6c] dark:text-[#A1A09A]">
                        Secure and reliable financial solutions tailored for you. Join us to manage your finances with ease.
                    </p>
                    <ul class="flex gap-3 text-sm leading-normal">
                        <li>
                            <Link
                                :href="route('login')"
                                class="inline-block rounded-sm border border-[#004085] bg-[#004085] px-5 py-1.5 text-sm leading-normal text-white hover:bg-[#002752] dark:border-[#EDEDEC] dark:hover:bg-[#EDEDEC] dark:hover:text-[#1C1C1A]"
                            >
                                Login
                            </Link>
                        </li>
                    </ul>
                </div>
                <div class="relative w-full shrink-0 overflow-hidden rounded-t-lg bg-[#DCEEFF] dark:bg-[#1D0002] lg:w-[438px] lg:rounded-r-lg lg:rounded-t-none">
                    <div class="absolute inset-0 flex items-center justify-center p-6">
                        <img src="/images/KMCLLOGO.jpeg" alt="KUWA Microfinance Logo" class="w-50 h-auto" />
                    </div>
                </div>
            </main>
        </div>
        <footer class="mt-6 text-sm text-[#6c757d] dark:text-[#A1A09A]">&copy; 2025 KUWA Microfinance. All Rights Reserved.</footer>
    </div>
</template>
