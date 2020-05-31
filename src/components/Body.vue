<template>
    <div class="flex flex-wrap justify-between p-4">
        <div v-for="(value, key) in this.info" :key="key"
             class="w-full md:w-1/2 lg:w-1/4 p-2 my-2 mx-2 h-64 rounded border-2 border-gray-500"
        >
            <div class="flex flex-col h-full content-center relative bg-white-400 p-4">
                <img :src="value.url" class="h-32 max-h-48">
                <p class="text-center h-24">{{ value.title }}</p>
                <div class="text-center w-full h-6 bg-yellow-200">
                    <p class="text-center">word</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Body',
        data() {
            return {
                info: [],
            };
        },
        async created() {
            await this.getImages();
        },
        methods: {
            async getImages() {
                const response = await fetch('https://meme-api.herokuapp.com/gimme/6');
                const resolvedResponse = await response.json();
                resolvedResponse.memes.forEach((meme) => {
                    this.info.push({url: meme.url, title: meme.title});
                })
            },
        },
    };
</script>