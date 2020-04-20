<script>
  export let weekday
  export let date
  export let min
  export let max
  export let condition
  export let conditionSlug
</script>

<div class="weather-forecast">
  <h3 class="weather-forecast__date">
    {weekday}, {date}
  </h3>
  <div class="weather-forecast__condition">
    <img src="/images/icons/{conditionSlug}.png" alt={condition} />
  </div>
  <div class="weather-forecast__condition-text">
    <p>
      {condition}
    </p>
  </div>
  <div class="weather-forecast_temperatures">
    <div class="weather-forecast_temperatures-min">
      <span class="weather-forecast_temperatures-number">{min}</span>
      <span class="weather-forecast_temperatures-description">Min</span>
    </div>
    <div class="weather-forecast_temperatures-max">
      <span class="weather-forecast_temperatures-number">{max}</span>
      <span class="weather-forecast_temperatures-description">Max</span>
    </div>
  </div>
</div>

<style>
  .weather-forecast {
    padding: 1em;
    border: 1px solid rgba(255, 255, 255, .2);
    min-width: 120px;
    margin-right: 1.5em;
    border-radius: 10px;
  }

  .weather-forecast__date {
    margin: 0;
    color: #fff;
    font-size: 1.2rem;
    margin-bottom: 1em;
    text-align: center;
  }

  .weather-forecast__condition {
    height: 80px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .weather-forecast__condition img {
    max-width: 50%;
  }

  .weather-forecast__condition-text {
    height: 35px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .weather-forecast__condition-text p {
    margin: 0;
    text-align: center;
    font-size: 1.2rem;
    color: #fff;
  }

  .weather-forecast_temperatures {
    display: flex;
    justify-content: center;
  }

  .weather-forecast_temperatures-min,
  .weather-forecast_temperatures-max {
    padding: 0 .5em;
    margin-top: 1em;
  }

  .weather-forecast_temperatures-number {
    display: block;
    font-size: 2.5rem;
    font-weight: bold;
    text-align: center;
    color: #fff;
  }

  .weather-forecast_temperatures-description {
    display: block;
    font-size: 1rem;
    text-align: center;
    color: #fff;
    letter-spacing: .1em;
    text-transform: uppercase;
    opacity: .6;
  }
</style>
