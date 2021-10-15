<script lang="ts">
  export let error: Error;
</script>

<div class="animate__animated animate__wobble error" role="alert">
  {error}
</div>

<style>
  .error {
    font-family: "Oswald", sans-serif;
    font-size: 25px;
    padding: 30px 100px;
    background: rgba(201, 12, 12, 0.25);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.18);
  }
</style>
