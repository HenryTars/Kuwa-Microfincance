<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import AppLayout from '@/layouts/AppLayout.vue';
import { UsersIcon, PlusCircleIcon } from '@heroicons/vue/24/solid';

const stats = [
    { title: 'Total Customers', value: '3,245', icon: UsersIcon, color: 'bg-blue-500' },
    { title: 'Active Customers', value: '2,100', icon: UsersIcon, color: 'bg-green-500' },
    { title: 'Pending Verification', value: '120', icon: UsersIcon, color: 'bg-yellow-500' }
];

const customers = [
    { name: 'Alice Johnson', email: 'alice@example.com', phone: '123-456-7890', status: 'Active' },
    { name: 'Michael Brown', email: 'michael@example.com', phone: '987-654-3210', status: 'Pending' },
    { name: 'Sarah White', email: 'sarah@example.com', phone: '555-666-7777', status: 'Active' }
];

const breadcrumbs: BreadcrumbItem[] = [
    { title: 'Dashboard', href: '/dashboard' },
    { title: 'Customers', href: '/customers' }
];
</script>

<template>
    <Head title="Customers" />
    <AppLayout :breadcrumbs="breadcrumbs">
        <!-- Stats Section -->
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
        </div>

        <!-- Customers Table Section -->
        <div class="relative min-h-[100vh] flex-1 rounded-xl border border-sidebar-border/70 dark:border-sidebar-border md:min-h-min p-4 bg-white dark:bg-gray-800 shadow-md">
            <h2 class="text-lg font-bold mb-2">Customers List</h2>
            <table class="w-full text-sm">
                <thead>
                    <tr class="border-b">
                        <th class="text-left py-2">Customer</th>
                        <th class="text-left py-2">Email</th>
                        <th class="text-left py-2">Phone</th>
                        <th class="text-left py-2">Status</th>
                        <th class="text-left py-2">Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="customer in customers" :key="customer.email">
                        <td class="py-2">{{ customer.name }}</td>
                        <td class="py-2">{{ customer.email }}</td>
                        <td class="py-2">{{ customer.phone }}</td>
                        <td class="py-2">{{ customer.status }}</td>
                        <td class="py-2">
                            <Link :href="`/customers/${customer.email}`" class="text-blue-600 hover:underline">View</Link>
                            <span class="mx-2">|</span>
                            <Link :href="`/customers/edit/${customer.email}`" class="text-green-600 hover:underline">Edit</Link>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>

        <!-- Quick Actions Section -->
        <div class="p-4 bg-white dark:bg-gray-800 rounded-lg shadow-md flex flex-col gap-3">
            <h2 class="text-lg font-bold">Quick Actions</h2>
            <Link :href="route('customers.create')" class="px-4 py-2 text-white bg-green-600 rounded-md hover:bg-green-700 text-center">
                <PlusCircleIcon class="w-5 h-5 inline mr-2" /> Add Customer
            </Link>
        </div>
    </AppLayout>
</template>
