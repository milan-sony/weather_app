<template>
    <div class="bg-blue-400 h-screen">
        <!-- Navbar -->
        <SiteNavigation />
        <!-- Search -->
        <div class="max-w-screen-sm items-center mx-auto p-5">
            <form class="flex items-center" @submit="submitForm">
                <label for="simple-search" class="sr-only">Search</label>
                <div class="relative w-full">
                    <input type="text" id="simple-search"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 focus:outline-none block w-full ps-10 p-2.5"
                        placeholder="Search for a city" v-model="formValue.place" required />
                </div>
                <button type="submit"
                    class="p-2.5 ms-2 text-sm font-medium text-white bg-blue-700 rounded-lg border border-blue-700 hover:bg-blue-500 focus:ring-4 focus:outline-none focus:ring-blue-300">
                    <svg class="w-4 h-4" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                        viewBox="0 0 20 20">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z" />
                    </svg>
                    <span class="sr-only">Search</span>
                </button>
            </form>
            <p class="text-start text-2xl pt-4 font-bold text-white">Search : {{ formValue.place }}</p>
        </div>
    </div>
</template>

<script>
// components
import SiteNavigation from '../components/SiteNavigation.vue'

export default {
    name: 'Home',
    components: {
        SiteNavigation
    },
    data() {
        return {
            formValue: {
                place: ''
            }
        }
    },
    methods: {
        submitForm(event) {
            event.preventDefault()
            console.log(this.formValue)
        }
    }
}
</script>