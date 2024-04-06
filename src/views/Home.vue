<template>
    <div class="bg-blue-400 h-screen">
        <!-- Navbar -->
        <SiteNavigation />
        <!-- Search -->
        <div class="max-w-screen-sm items-center mx-auto p-5">
            <form class="flex items-center" @submit.prevent="searchPlace">
                <label for="simple-search" class="sr-only">Search</label>
                <div class="relative w-full">
                    <div class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none">
                        <svg class="w-4 h-4 text-blue-700" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                            fill="none" viewBox="0 0 20 20">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z" />
                        </svg>
                    </div>
                    <input type="text" id="simple-search"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 focus:outline-none block w-full ps-10 p-2.5"
                        placeholder="Search for a city" v-model="formValue.place" @input="checkInput" />
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
            <p v-if="errorMsg" class="text-white font-semibold">Please enter a place</p>
            <div v-if="searchResult">
                <p class="text-start text-xl pt-4 pb-2 font-bold text-white">Search result for: {{ formValue.place }}
                </p>
                <div class="bg-white p-4 rounded-md">
                    <div v-for="place in searchResult" :key="place.id">
                        <button class="hover:text-blue-700 hover:font-bold font-semibold p-3">{{ place.name }}, {{
                place.region }}, {{ place.country }}</button>
                        <hr>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
// components
import SiteNavigation from '../components/SiteNavigation.vue'

import axios from 'axios'

export default {
    name: 'Home',
    components: {
        SiteNavigation
    },
    data() {
        return {
            formValue: {
                place: ''
            },
            searchResult: '',
            errorMsg: false
        }
    },
    methods: {
        async searchPlace() {
            if (this.formValue.place !== '') {
                console.log(this.formValue.place)
                await axios.get(`http://api.weatherapi.com/v1/search.json?key=a0181bd8c8b14fa99aa84630232101&q=${this.formValue.place}`).then((response) => {
                    console.log(response.data)
                    this.searchResult = response.data
                    console.log('Result', this.searchResult)
                }).catch((err) => {
                    console.log(err)
                })
            }else{
                this.errorMsg = true
            }
        },
        checkInput() {
            if (this.formValue.place === '') {
                this.searchResult = ''
            }else{
                this.errorMsg = false
            }
        }
    }
}
</script>