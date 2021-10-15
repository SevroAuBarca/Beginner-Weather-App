<script lang="ts">
  import type { WeatherDataInterface } from "../Typescript/Weather";
  import Err from "./Error.svelte";
  import Loader from "./Loader.svelte";
  import WeatherData from "./WeatherData.svelte";
  import search from "../assets/S.png";

  let city = "";
  const APIkey = "3a4466f71292506dd9a823d5098fe82a";

  const getWeatherData = async (city: string = "paris") => {
    const URL = `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${APIkey}`;
    console.log(URL);
    if (city.trim() === "") {
      throw new Error("Fill the text");
    }

    const res: Response = await fetch(URL);

    if (!res.ok) {
      throw new Error("Data not found");
    }

    const data = await res.json();
    return data;
  };

  const handleSubmit = () => {
    promise = getWeatherData(city);
    city = "";
  };

  let promise = getWeatherData();
</script>

<div class="container">
  <div class="row">
    <div class="form">
      <form class="formData" on:submit|preventDefault={handleSubmit}>
        <label>
          <input bind:value={city} type="text" class="txt" />
        </label>
        <button type="submit" class="submit"
          ><img class="search" src={search} alt="search" /></button
        >
      </form>
    </div>
    {#await promise}
      <div class="cont">
        <Loader />
      </div>
    {:then { main: { temp, temp_max, temp_min }, name, sys: { country }, weather }}
      <WeatherData {temp} {temp_max} {temp_min} {name} {country} {weather} />
    {:catch error}
      <Err {error} />
    {/await}
  </div>
</div>

<style>
  .cont {
    display: flex;
    justify-content: center;
  }
  .form {
    z-index: 200;
    padding-bottom: 10vh;
    display: flex;
    justify-content: center;
  }
  .formData {
    display: flex;
    align-items: center;
  }
  .txt {
    height: 20px;
    border-radius: 5px;
  }
  .submit {
    background: transparent;
    border: none;
    cursor: pointer;
  }
  .search {
    width: 30px;
    height: 30px;
  }
</style>
