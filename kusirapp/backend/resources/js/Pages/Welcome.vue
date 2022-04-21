<script setup>
import { Head, Link } from "@inertiajs/inertia-vue3";

const navigation = [
    { name: "Dashboard", href: "#", current: true },
    { name: "Team", href: "#", current: false },
    { name: "Projects", href: "#", current: false },
    { name: "Calendar", href: "#", current: false },
];

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
});
</script>

<template>
    <Head title="Welcome" />
    <nav class="bg-gray-800 px-6 py-4">
        <div class="hidden sm:block">
            <div class="mx-auto max-w-7xl">
                <div class="relative flex justify-between">
                    <div class="items-start">
                        <img
                            class="block h-8 w-auto"
                            src="https://tailwindui.com/img/logos/workflow-logo-indigo-500-mark-white-text.svg"
                            alt="Workflow"
                        />
                    </div>
                    <div class="flex items-center space-x-4">
                        <a
                            v-for="item in navigation"
                            :key="item.name"
                            :href="item.href"
                            :class="[
                                item.current
                                    ? 'bg-gray-900 text-white'
                                    : 'text-gray-300 hover:bg-gray-700 hover:text-white',
                                'px-3 py-2 rounded-md text-sm font-medium',
                            ]"
                            :aria-current="item.current ? 'page' : undefined"
                            >{{ item.name }}</a
                        >
                    </div>
                    <div class="flex items-end space-x-4">
                        <Link
                            v-if="$page.props.user"
                            :href="route('dashboard')"
                            class="bg-gray-900 hover:bg-gray-700 text-white hover:text-white px-3 py-2 rounded-md text-sm font-medium"
                        >
                            Dashboard
                        </Link>

                        <template v-else>
                            <Link
                                :href="route('login')"
                                class="bg-gray-900 hover:bg-gray-700 text-white hover:text-white px-3 py-2 rounded-md text-sm font-medium"
                            >
                                Masuk
                            </Link>

                            <Link
                                v-if="canRegister"
                                :href="route('register')"
                                class="bg-gray-900 hover:bg-gray-700 text-white hover:text-white px-3 py-2 rounded-md text-sm font-medium"
                            >
                                Register
                            </Link>
                        </template>
                    </div>
                </div>
            </div>
        </div>

        <div class="block sm:hidden">
            <div class="relative mx-auto max-w-7xl">
                <div class="flex items-center justify-center">
                    <div class="items-center">
                        <img
                            class="block h-8 w-auto lg:hidden"
                            src="https://tailwindui.com/img/logos/workflow-mark-indigo-500.svg"
                            alt="Workflow"
                        />
                    </div>
                </div>
            </div>
        </div>
    </nav>
</template>
