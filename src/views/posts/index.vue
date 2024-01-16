<script setup>

//import ref and onMounted
import { ref, onMounted } from 'vue';

//import api
import api from '../../api';

//define state
const posts = ref([]);

//method fetchDataPosts
const fetchDataPosts = async () => {

    //fetch data 
    await api.get('/api/posts')

        .then(response => {

            //set response data to state "posts"
            posts.value = response.data.data.data

        });
}

//run hook "onMounted"
onMounted(() => {

    //call method "fetchDataPosts"
    fetchDataPosts();
});

//method deletePost
const deletePost = async (id) => {

    //delete post with API
    await api.delete(`/api/posts/${id}`)
        .then(() => {

            //call method "fetchDataPosts"
            fetchDataPosts();
        })

};

</script>

<template>
    <div>
        <div class="py-3 px-5 bg-slate-100 text-slate-500">Home / <span class="text-slate-400">Dashboard</span></div>
        <div class="m-3 p-3">
            <div>
                <router-link :to="{ name: 'posts.create' }" class="p-2 bg-[#2eb85c] text-white rounded-md">Add
                    New</router-link>
            </div>
            <div class="relative mt-5 overflow-x-auto shadow-md sm:rounded-lg">
                <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                    <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                        <tr>
                            <th scope="col" class="px-6 py-3">Image</th>
                            <th scope="col" class="px-6 py-3">Title</th>
                            <th scope="col" class="px-6 py-3">Content</th>
                            <th scope="col" class="px-6 py-3">Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-if="posts.length == 0" class="odd:bg-white even:bg-gray-50 border-b">
                            <td colspan="4" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                                <div class="alert alert-danger mb-0">
                                    Data Belum Tersedia!
                                </div>
                            </td>
                        </tr>
                        <tr v-else v-for="(post, index) in posts" :key="index" class="odd:bg-white even:bg-gray-50 border-b">
                            <td class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                                <img :src="post.image" width="200" class="rounded-3" />
                            </td>
                            <td>{{ post.title }}</td>
                            <td>{{ post.content }}</td>
                            <td>
                                <router-link :to="{ name: 'posts.edit', params: { id: post.id } }"
                                    class="m-1 p-2 bg-gray-500 text-white rounded-md">EDIT</router-link>
                                <button @click.prevent="deletePost(post.id)"
                                    class="m-1 p-2 bg-red-500 text-white rounded-md">DELETE</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>