<template>
    
    <video autoplay v-bind:muted="is_muted" v-bind:src="NovoVideo()" @ended="NovoVideo()"></video>
    <div class="content">
        <button @click="is_muted = !is_muted">{{ is_muted }}</button>
    </div>

</template>

<script lang="ts">
    export default {
        setup(){
            const is_muted = ref(true)

            return {
                is_muted
            }
        },
        methods: {
            NovoVideo(): string{ 

                let videos = [
                    "juvenil/2024/videos/pio-x/Alleluja Christe.mp4",
                    "juvenil/2024/videos/pio-x/Signore Delle Cime.mp4"
                ]

                return videos[Math.floor(Math.random() * videos.length)]
            }
        }
    }
</script>

<style lang="scss">
    video{
        position: fixed;
        right: 0;
        bottom: 0;
        min-width: 100%;
        min-height: 100%;
    }

    .content {
        position: fixed;
        bottom: 0;
        width: 100%;
        padding: 20px;
    }
</style>