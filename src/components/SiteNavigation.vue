<template>
    <nav class="bg-blue-700">
        <div class="max-w-screen-lg items-center mx-auto p-4">
            <RouterLink :to="{ name: 'Home' }">
                <div class="flex items-center space-x-3 rtl:space-x-reverse">
                    <span
                        class="self-center text-2xl font-extrabold uppercase tracking-wider whitespace-nowrap text-white dark:text-white max-md:pb-4"><i
                            class="fa-solid fa-cloud-sun-rain"></i> Weathery
                    </span>
                </div>
            </RouterLink>
        </div>
    </nav>
</template>

<script>
import { RouterLink } from 'vue-router';

export default {
    name: 'SiteNavigation'
}
</script>