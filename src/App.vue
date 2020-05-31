<template>
    <div id="app" class="container mx-auto w-full h-full pt-4">
        <custom-header/>
        <main-container/>
    </div>
</template>

<script>
    import Header from './components/Header';
    import Body from './components/Body';

    export default {
        name: 'App',
        components: {
            CustomHeader: Header,
            MainContainer: Body,
        },
    };
</script>