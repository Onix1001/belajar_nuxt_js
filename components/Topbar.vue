<template>
    <div class="w-full h-14 p-2 bg-blue-600 text-white text-xl font-bold uppercase">
        <h1>{{ title }}</h1>
    </div>
</template>

<script>
export default {
    props: {
        title: String,
    }
}
</script>