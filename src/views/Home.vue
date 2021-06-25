<template>
  <div id="Home">
    <div class="searchBar">
      <input
        id="searchQueryInput"
        type="text"
        name="searchQueryInput"
        placeholder="Search city names"
        v-model="query"
        @keypress="fetchWeather"
      />
    </div>
    <div class="container-fluid">
      <div class="row justify-content-center">
        <div class="col-12 col-md-4 col-sm-12 col-xs-12">
          <div class="card p-4" v-if="typeof weather.main != 'undefined'">
            <div class="d-flex">
              <h6 class="flex-grow-1">
                {{ weather.name }}, {{ weather.sys.country }}
              </h6>
              <h6>{{ dateBuilder() }}</h6>
            </div>
            <div class="d-flex flex-column temp mt-5 mb-3">
              <h1 class="mb-0 font-weight-bold" id="heading">
                {{ Math.round(weather.main.temp) }}°c
              </h1>
              <span class="small grey">{{ weather.weather[0].main }}</span>
            </div>
            <div class="d-flex">
              <div class="temp-details flex-grow-1">
                <p class="my-1">
                  <img src="https://i.imgur.com/B9kqOzp.png" height="17px" />
                  <span> 40 km/h </span>
                </p>
                <p class="my-1">
                  <i class="fa fa-tint mr-2" aria-hidden="true"></i>
                  <span> 84% </span>
                </p>
                <p class="my-1">
                  <img src="https://i.imgur.com/wGSJ8C5.png" height="17px" />
                  <span> 0.2h </span>
                </p>
              </div>
              <div v-if="weather.main.temp >= 26">
                <img
                  src="https://img.icons8.com/cute-clipart/64/000000/sun.png"
                />
              </div>
              <div
                v-else-if="weather.main.temp <= 26 && weather.main.temp >= 17"
              >
                <img
                  src="https://img.icons8.com/color-glass/96/000000/wind.png"
                />
              </div>
              <div v-else-if="weather.main.temp <= 16">
                <img
                  src="https://img.icons8.com/cute-clipart/64/000000/cloud.png"
                />
              </div>
              <div v-else-if="weather.main.temp <= 0">
                <img src="https://img.icons8.com/clouds/100/000000/snow.png" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      api_key: "151ac4e2b3944ba738e3208ee3be382d",
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {},
    };
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(
          `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`
        )
          .then((res) => {
            return res.json();
          })
          .then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    },
    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December",
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday",
      ];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year}`;
    },
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Marcellus&display=swap");

html,
body {
  height: 100%;
}

* {
  margin: 4px;
}

body {
  background-color: #a5a5b1;
  display: grid;
  place-items: center;
}

.card {
  background-color: #ffffff;
  border-radius: 50px;
  color: #6f707d;
  font-family: "Marcellus", serif;
}

#heading {
  font-size: 55px;
  color: #2b304d;
}

.temp {
  place-items: center;
}

.temp-details > p > span,
.grey {
  color: #a3acc1;
  font-size: 12px;
}

.fa {
  color: #a5a5b1;
}

*:focus {
  outline: none;
}

.searchBar {
  width: 40%;
  display: flex;
  flex-direction: row;
  margin-right: auto;
  margin-left: auto;
}
@media only screen and (max-width: 600px) {
  .searchBar {
    width: 70%;
    display: flex;
    flex-direction: row;
    margin-right: auto;
    margin-left: auto;
  }
}

#searchQueryInput {
  width: 100%;
  height: 2.8rem;
  background: #f5f5f5;
  outline: none;
  border: none;
  border-radius: 1.625rem;
  padding: 0 3.5rem 0 1.5rem;
  font-size: 1rem;
}
</style>
