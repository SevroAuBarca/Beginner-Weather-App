<script lang="ts">
  import { onMount } from "svelte";
  import Weather from "./components/Weather.svelte";

  let heroVideo;
  onMount(() => {
    if (typeof heroVideo.loop == "boolean") {
      heroVideo.loop = true;
    } else {
      heroVideo.on(
        "ended",
        () => {
          this.currentTime = 0;
          this.play();
        },
        false
      );
    }
  });
</script>

<main>
  <video
    src="https://cdn.videvo.net/videvo_files/video/free/2019-12/large_watermarked/190915_B_01_Timelapse%20Danang_05_preview.mp4
      "
    class="screen"
    muted
    loop
    autoplay
    bind:this={heroVideo}
  />
  <h1 class="title">Weather App</h1>

  <div class="container">
    <Weather />
  </div>
</main>

<style>
  main {
    height: 100vh;
    position: relative;
  }
  .screen {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    background-repeat: no-repeat;
    object-fit: cover;
    z-index: -100;
  }

  .title {
    height: 15vh;
    padding-top: 0;
    margin-top: 0;
    text-align: center;
    font-family: "Oswald", sans-serif;
    font-weight: 400;
    font-size: 50px;
    z-index: 200;
  }

  .container {
    height: 80vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>
