<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import AppLayout from '@/layouts/AppLayout.vue';
import { BanknotesIcon, UsersIcon, WalletIcon } from '@heroicons/vue/24/solid';

const stats = [
    { title: 'Total Customers', value: '3,245', icon: UsersIcon, color: 'bg-blue-500' },
    { title: 'Active Loans', value: '450', icon: BanknotesIcon, color: 'bg-green-500' },
    { title: 'Total Savings', value: '$3.8M', icon: WalletIcon, color: 'bg-yellow-500' }
];

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: '/dashboard',
    },
];
</script>

<template>
    <Head title="Dashboard" />
    <AppLayout :breadcrumbs="breadcrumbs">
        <div class="flex h-full flex-1 flex-col gap-4 rounded-xl p-4">
            <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
                <div v-for="stat in stats" :key="stat.title" class="p-5 rounded-lg shadow bg-white dark:bg-gray-800 flex items-center">
                    <div :class="[stat.color, 'text-white text-3xl p-3 rounded-full']">
                        <component :is="stat.icon" class="w-8 h-8" />
                    </div>
                    <div class="ml-4">
                        <p class="text-gray-600 dark:text-gray-300 text-sm">{{ stat.title }}</p>
                        <p class="text-2xl font-bold text-gray-900 dark:text-gray-100">{{ stat.value }}</p>
                    </div>
                </div>
            </div>
            <div class="relative min-h-[100vh] flex-1 rounded-xl border border-sidebar-border/70 dark:border-sidebar-border md:min-h-min p-4 bg-white dark:bg-gray-800 shadow-md">
                <h2 class="text-lg font-bold mb-2">Recent Transactions</h2>
                <table class="w-full text-sm">
                    <thead>
                        <tr class="border-b">
                            <th class="text-left py-2">Customer</th>
                            <th class="text-left py-2">Amount</th>
                            <th class="text-left py-2">Date</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td class="py-2">Alice Johnson</td>
                            <td class="py-2">$700</td>
                            <td class="py-2">2025-03-04</td>
                        </tr>
                        <tr>
                            <td class="py-2">Michael Brown</td>
                            <td class="py-2">$1,500</td>
                            <td class="py-2">2025-03-03</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="p-4 bg-white dark:bg-gray-800 rounded-lg shadow-md flex flex-col gap-3">
                <h2 class="text-lg font-bold">Quick Actions</h2>
                <Link :href="route('dashboard')" class="px-4 py-2 text-white bg-green-600 rounded-md hover:bg-green-700 text-center">
                    Apply for Loan
                </Link>
                <Link :href="route('dashboard')" class="px-4 py-2 text-white bg-blue-600 rounded-md hover:bg-blue-700 text-center">
                    Add Savings
                </Link>
            </div>
        </div>
    </AppLayout>
</template>
