<template>

        <h1 class="text-lg mb-4">Create</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sky-500 text-sm">Back</Link>
        </div>
        <form @submit.prevent="store">
            <div class="mb-2">
                <input v-model="title" class="w-full border rounded-full border-cyan-500" type="text" placeholder="title">
                <div v-if="errors.title" class="text-red-500">{{ errors.title }}</div>
            </div>
            <div>
                <textarea v-model="content" class="w-full border rounded-full border-cyan-500" placeholder="content"></textarea>
                <div v-if="errors.content" class="text-red-500">{{ errors.content }}</div>
            </div>
            <div>
                <button class="ml-auto hover:text-cyan-500 hover:bg-white border border-cyan-500 block p-2 w-32 bg-cyan-500 rounded-full text-center text-white" type="submit">Store</button>
            </div>
        </form>

</template>
<script>
import {Link} from '@inertiajs/vue3'
import MainLayout from '@/Layouts/MainLayout.vue'
export default {
    name: "Create",
    components :{
        Link
    },
    layout: MainLayout,
    data() {
        return {
            title: '',
            content: '',
        };
    },
    props: [
        'errors'
    ],
    methods: {
        store(){
            this.$inertia.post('/posts', {title: this.title, content: this.content})
        }
    },
}
</script>
<style scoped>
</style>