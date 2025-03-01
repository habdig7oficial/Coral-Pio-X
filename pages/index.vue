<template>
    <video autoplay loop ref="bg_video" v-bind:muted="is_muted" :class="{ normal: is_muted == false }"
        v-bind:src="playing"></video>
        
    <div data-bs-theme="dark" class="content d-flex flex-column ">
        <h1 class="piox text-center white-shadow">
            Corais Pio X
        </h1>

        <div class="d-flex align-items-center justify-content-center my-3 flex-wrap flex-lg-row flex-column">
            <Card text="Infantil" class="infantil my-sm-3" img="/images/logo.png" to="/infantil"></Card>
            <Card text="Infanto-Juvenil" class="juvenil my-sm-3" img="/images/logo.png" to="/juvenil"></Card>
            <Card text="Adulto" class="piox my-sm-3" img="/images/logo.png" to="/adulto"></Card>
        </div>

        <div class="align-self-center">
            <button class="btn btn-warning d-flex flex-row" @click="Mute()">
                <i :class="{ 'bi bi-volume-mute-fill': is_muted == false, 'bi bi-volume-up-fill': is_muted }"></i>
                Ouça Agora!
            </button>
        </div>

        <div class="m-4"></div>

        <a href="https://piox.com.br/" class="text-center fixed-bottom text-info h4 text-decoration-none">Site Completo do <span class="piox text-info">Pio X</span></a>



    </div>

</template>

<script lang="ts">
import Card from '~/components/Card.vue';

export default {
    setup() {
        let videos = [
            "juvenil/2024/videos/pio-x/Alleluja Christe.mp4",
            "juvenil/2024/videos/pio-x/Signore Delle Cime.mp4",
            "juvenil/2024/videos/pio-x/Carol of the Bells.mp4",
            "juvenil/2024/videos/pio-x/Il Caffè della Peppina.mp4"
        ]

        const is_muted = ref(true)
        const playing = ref(videos[Math.floor(Math.random() * videos.length)])
        const bg_video = useTemplateRef("bg_video")

        console

        return {
            is_muted,
            playing,
            videos,
            bg_video
        }
    },
    methods: {
        NovoVideo() {
            let novo_video = this.videos[Math.floor(Math.random() * this.videos.length)]
            if (novo_video == this.playing) {
                this.NovoVideo()
            }
            else {
                this.playing = novo_video
            }

        },
        Mute() {
            this.is_muted = !this.is_muted;

            /*
            if (this.is_muted == true) {
                var fadeAudio = setInterval(() => {
                    // Only fade if past the fade out point or not at zero already
                    if (this.bg_video.volume != 0.0) {
                        this.bg_video.volume -= 0.1;
                    }
                    // When volume at zero stop all the intervalling
                    if (this.bg_video.volume === 0.0) {
                        clearInterval(fadeAudio);
                    }
                }, 200);
            }
            else if (this.is_muted == false) {
                if (this.is_muted == true) {
                    var fadeAudio = setInterval(() => {
                        // Only fade if past the fade out point or not at zero already
                        if (this.bg_video.volume != 1.0) {
                            this.bg_video.volume += 0.1;
                        }
                        // When volume at zero stop all the intervalling
                        if (this.bg_video.volume === 1.0) {
                            clearInterval(fadeAudio);
                        }
                    }, 200);
                }

            }
                */
        }
    }
}
</script>

<style lang="scss">
video {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    min-width: 100%;
    min-height: 100%;
    filter: grayscale(70%) blur(4px);
    animation: to_effect 5s;
}

.normal {
    filter: none;
    animation: to_normal 2s;
}

@keyframes to_normal {
    from {
        filter: grayscale(70%) blur(4px);
    }

    to {
        filter: none;
    }
}

@keyframes to_effect {
    from {
        filter: none;
    }

    to {
        filter: grayscale(70%) blur(4px);
    }
}


.content {
    position: absolute;
    top: 0;
    width: 100%;
    padding: 20px;
    overflow-y: scroll;
    overflow-x: scroll;
}

.img{
    max-width: 11rem;
}

.footer-geral{
    position: fixed;
    bottom: 0;
    
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity .5s
}

.fade-enter,
.fade-leave-to {
    opacity: 0
}
</style>

<!--            <a href="/juvenil" class="d-flex flex-column align-items-center justify-content-center text-decoration-none">
                <div class="p-2" style="height: 9rem; background-color: white;">
                    <p>Desenho da Kelly</p>
                </div>
                <h2 style="--bs-bg-opacity: .8;" class="juvenil my-1 mx-5 px-3 py-2 pt-3 text-center text-bg-light rounded-pill">Infanto-Juvenil</h2>
            </a>-->