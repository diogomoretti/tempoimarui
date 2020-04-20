<script>
  export let weekday
  export let temperature
  export let condition
  export let conditionSlug
</script>

<div class="weather-item">
  <h2 class="weather-item__date">
    Hoje, {weekday}
  </h2>
  <div class="weather-item__condition">
    <div class="weather-item__condition-image">
      <img src="/images/icons/{conditionSlug}.png" alt={condition} />
    </div>
    <div class="weather-item__condition-temp">
      <span class="weather-item__temperature">{temperature}</span>
    </div>
  </div>
  <p class="weather-item__condition-text">
    {condition}
  </p>
</div>

<style>
  .weather-item {
    padding: 1em;
  }

  .weather-item__date {
    margin: 0;
    color: #fff;
    font-size: 2rem;
    font-weight: bold;
    text-align: center;
    margin-bottom: 1em;
  }

  .weather-item__condition {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .weather-item__condition-image {
    padding-right: 1em;
    display: flex;
    align-items: center;
    margin-left: -1.6em;
  }

  .weather-item__condition-temp {
    padding-left: 1em;
  }

  .weather-item__condition img {
    max-width: 60px;
  }

  .weather-item__temperature {
    position: relative;
    display: inline-block;
    font-size: 6rem;
    color: #fff;
    font-weight: 900;
    line-height: 1;
  }

  .weather-item__temperature:after {
    content: 'o';
    font-size: .4em;
    position: absolute;
    top: .3em;
    right: -.7em;
  }

  .weather-item__condition-text {
    color: #fff;
    font-size: 1.6rem;
    padding-top: .5em;
    text-align: center;
  }
</style>
