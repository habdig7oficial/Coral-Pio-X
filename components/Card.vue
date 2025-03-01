<template>
    <a :href="to" class="d-flex flex-column align-items-center justify-content-center text-decoration-none">
        <img class="img rounded" :src="img">
        <h2 style="--bs-bg-opacity: .8;" :class="classes" class="my-2 mx-5 px-3 py-2 text-center text-bg-light rounded-pill">{{ text }}</h2>
    </a>
</template>

<script>
    export default {
        props:{
            text: String,
            classes: String,
            img: String,
            to: String
        },
        setup(props){
            
        }
    }
</script>