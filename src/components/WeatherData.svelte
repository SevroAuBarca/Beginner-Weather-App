<script lang="ts">
  export let temp, temp_max, temp_min, name, country, weather;
</script>

<div class="animate__animated animate__zoomIn glass">
  <h1 class="text">
    <img
      class="bg-secondary"
      src={`http://openweathermap.org/img/wn/${weather[0].icon}@2x.png`}
      alt={weather[0].main}
    />
    {temp}°C
  </h1>
  <h4>City: <span class="fw-bold">{name}, {country}</span></h4>
  <h4>Weather: <span class="fw-bold">{weather[0].description}</span></h4>
  <div class="animate__animated animate__zoomIn ">
    <h4>
      Max Temperature: <span class="maxTemp">{temp_max} °C</span>
    </h4>
    <h4>
      Min Temperature: <span class="minTemp">{temp_min} °C</span>
    </h4>
  </div>
</div>

<style>
  .glass {
    margin-top: 15px;
    width: 110%;
    font-family: "Oswald", sans-serif;
    text-align: center;
    background: rgba(25, 17, 152, 0.45);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.18);
  }
  .text {
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
