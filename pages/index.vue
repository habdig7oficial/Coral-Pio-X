<template >
    
    <video :key="played" autoplay loop v-bind:muted="is_muted" v-bind:src="playing"></video>
    <div data-bs-theme="dark" class="content">
        <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis quia totam delectus illo natus nisi iure omnis maiores perspiciatis pariatur officia nulla animi ipsam, velit ullam porro facere eveniet. Expedita!</h1>
        <button class="btn btn-warning" @click="is_muted = !is_muted">
           habilitar Som
        </button>
    </div>

</template>

<script lang="ts">
    export default {
        setup(){
            let videos = [
                    "juvenil/2024/videos/pio-x/Alleluja Christe.mp4",
                    "juvenil/2024/videos/pio-x/Signore Delle Cime.mp4",
                    "juvenil/2024/videos/pio-x/Carol of the Bells.mp4",
                    "juvenil/2024/videos/pio-x/Il Caffè della Peppina.mp4"
            ]

            const is_muted = ref(true)
            const playing  = ref(videos[Math.floor(Math.random() * videos.length)])
            const played = ref(0)

            console

            return {
                is_muted,
                playing,
                videos,
                played
            }
        },
        methods: {
            NovoVideo(){ 
                let novo_video = this.videos[Math.floor(Math.random() * this.videos.length)]
                if (novo_video == this.playing) {
                    this.NovoVideo()
                }
                else{
                    this.playing = novo_video
                    this.played++
                }
                
            }
        }
    }
</script>

<style lang="scss">
    @use "bootstrap";
    video{
        position: fixed;
        top:0;
        bottom: 0;
        left: 0;
        right: 0;
        min-width: 100%;
        min-height: 100%;
    }

    .content {
        position: fixed;
        top: 0;
        width: 100%;
        padding: 20px;
    }
</style>