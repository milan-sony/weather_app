<template>
    <nav class="bg-blue-700">
        <div class="max-w-screen-lg items-center mx-auto p-4">
            <RouterLink :to="{ name: 'Home' }">
                <div class="flex justify-between items-center ">
                    <span
                        class="self-center text-2xl font-extrabold uppercase tracking-wider whitespace-nowrap text-white dark:text-white max-md:pb-4"><i
                            class="fa-solid fa-cloud-sun-rain"></i> Weathery
                    </span>
                    <div id="app" class="text-right font-bold text-sm text-white ">
                        {{ new Date().toLocaleString(
                            'en-us',{
                                weekday: 'long',
                                year: 'numeric',
                                month: 'long',
                                day: 'numeric'
                            }
                        ) }}
                    </div>
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