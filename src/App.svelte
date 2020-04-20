<script>
  import { onMount } from 'svelte'
  import { API_URL } from './services/api'
  import moment from 'moment'
  import 'moment/locale/pt-br'
  import WeatherItem from './components/weather-item.svelte'
  import WeatherForecast from './components/weather-forecast.svelte'

  moment.locale('pt-BR')

  let weather
  let today
  let temperature
  let condition
  let condition_slug
  let today_weekday
  let forecast = []

  function fetchData (api) {
    return fetch(api).then(response => response.json())
  }

  onMount(async () => {
    const response = await fetchData(API_URL)
    weather = response.results
    today = moment(weather.date, 'DD/MM/YYYY')
    today_weekday = today.format('dddd')
    temperature = weather.temp
    condition = weather.description
    condition_slug = weather.condition_slug
    forecast = weather.forecast
  })
</script>

<main>
  {#if weather}
    <header class="header">
      <h1 class="header-title">
        Imaruí, SC
        <span>Brasil</span>
      </h1>
    </header>
    <section>
      <WeatherItem
        weekday={today_weekday}
        temperature={temperature}
        condition={condition}
        conditionSlug={condition_slug}
      />
    </section>
    <section class="forecast">
      <div class="forecast-list">
        {#each forecast as item, i}
          {#if i > 0}
            <WeatherForecast
              weekday={item.weekday}
              date={item.date}
              min={item.min}
              max={item.max}
              condition={item.description}
              conditionSlug={item.condition}
            />
          {/if}
        {/each}
      </div>
    </section>
  {:else}
    <p class='loading'>Carregando...</p>
  {/if}
</main>

<style>
  @font-face {
    font-family: 'Gilmer';
    src: url('/fonts/gilmer_bold-webfont.woff2') format('woff2'),
         url('/fonts/gilmer_bold-webfont.woff') format('woff');
    font-weight: bold;
  }

  @font-face {
    font-family: 'Gilmer';
    src: url('/fonts/gilmer_heavy-webfont.woff2') format('woff2'),
         url('/fonts/gilmer_heavy-webfont.woff') format('woff');
    font-weight: 900;
  }

  @font-face {
    font-family: 'Gilmer';
    src: url('/fonts/gilmer_regular-webfont.woff2') format('woff2'),
         url('/fonts/gilmer_regular-webfont.woff') format('woff');
    font-weight: normal;
  }

  :global(*) {
    box-sizing: inherit;
  }

  :global(html) {
    font-size: 10px;
    box-sizing: border-box;
  }

  :global(body) {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 1rem;
    margin: 0;
    padding: 0;
    font-family: 'Gilmer', sans-serif;
    background: rgb(51,108,238);
    background: linear-gradient(180deg, rgba(51,108,238,1) 0%, rgba(115,158,254,1) 100%);
  }

  main {
    padding: 3em;
    width: 100vw;
    height: calc(100vh - 100px);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .header {
    padding-top: 1em;
    color: #000;
  }

  .header-title {
    margin: 0;
    font-size: 2.5rem;
    color: #fff;
    text-indent: -1px;
  }

  .header-title span {
    font-size: .5em;
    display: block;
    font-weight: normal;
    letter-spacing: .3em;
    margin-top: .2em;
    text-transform: uppercase;
    text-indent: 0;
  }

  .forecast {
    display: block;
    max-width: 100%;
    overflow: auto;
  }

  .forecast-list {
    display: flex;
  }

  .loading {
    color: #fff;
    text-align: center;
    text-transform: uppercase;
    font-size: 1.4rem;
  }
</style>
