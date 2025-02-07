<template>
    <video autoplay loop ref="bg_video" v-bind:muted="is_muted" :class="{ normal: is_muted == false }"
        v-bind:src="playing"></video>
    <div data-bs-theme="dark" class="content">
        <h1>Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis quia totam delectus illo natus nisi iure
            omnis maiores perspiciatis pariatur officia nulla animi ipsam, velit ullam porro facere eveniet. Expedita!
        </h1>
        <button class="btn btn-warning"  @click="Mute()">
            <i :class="{'bi bi-volume-mute-fill': is_muted == false, 'bi bi-volume-up-fill': is_muted }"></i>
            Som
        </button>

    </div>

</template>

<script lang="ts">
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
    position: fixed;
    top: 0;
    width: 100%;
    padding: 20px;
}
</style>