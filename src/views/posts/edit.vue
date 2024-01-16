<script setup>
    //import ref
    import { ref, onMounted } from "vue";

    //import router
    import { useRouter, useRoute } from 'vue-router';

    //import api
    import api from "../../api";

    //init router
    const router = useRouter();

    //init route
    const route = useRoute();
    
    //define state
    const image = ref("");
    const title = ref("");
    const content = ref("");
    const errors = ref([]);

    //onMounted
    onMounted( async () => {

        //fetch detail data post by ID
        await api.get(`/api/posts/${route.params.id}`)
        .then(response => {
            
            //set response data to state
            title.value = response.data.data.title
            content.value = response.data.data.content
        });
    })

    //method for handle file changes
    const handleFileChange = (e) => {
        //assign file to state
        image.value = e.target.files[0];
    };

    //method "updatePost"
    const updatePost = async () => {

        //init formData
        let formData = new FormData();

        //assign state value to formData
        formData.append("image", image.value);
        formData.append("title", title.value);
        formData.append("content", content.value);
        formData.append("_method", "PATCH");

        //store data with API
        await api.post(`/api/posts/${route.params.id}`, formData)
        .then(() => {
            //redirect
            router.push({ path: "/posts" });
        })
        .catch((error) => {
            //assign response error data to state "errors"
            errors.value = error.response.data;
        });
    };
</script>

<template>
    <div>
        <div class="py-3 px-5 bg-slate-100 text-slate-500">Home / <span class="text-slate-400">Edit Post</span></div>
    </div>
    <div class="relative m-5 p-4 bg-white rounded-md border-[1px] border-slate-300">
        <form @submit.prevent="updatePost()">
            <div class="mb-5">
                <input type="file" class="w-full max-w-2xl p-2 bg-white rounded-md border-[1px] border-slate-300" @change="handleFileChange($event)">
                <div v-if="errors.image" class="alert alert-danger mt-2">
                    <span>{{ errors.image[0] }}</span>
                </div>
            </div>
            <div class="mb-5">
                <input type="text" class="w-full max-w-2xl p-2 bg-white rounded-md border-[1px] border-slate-300" v-model="title" placeholder="Title Post">
                <div v-if="errors.title" class="alert alert-danger mt-2">
                    <span>{{ errors.title[0] }}</span>
                </div>
            </div>
            <div class="mb-3">
                <label class="form-label fw-bold">Content</label>
                <textarea class="block p-2 w-full max-w-2xl text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-blue-500 focus:border-blue-500" v-model="content" rows="5" placeholder="Content Post"></textarea>
                <div v-if="errors.content" class="alert alert-danger mt-2">
                    <span>{{ errors.content[0] }}</span>
                </div>
            </div>
            <button type="submit" class="p-2 rounded-md bg-[#3399FF] text-white">Update</button>
        </form>
    </div>
</template>