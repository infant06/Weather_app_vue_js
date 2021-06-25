# Weather App by Vue.js
## _Current & Forecast weather data collection by_

[![N|Solid](https://openweathermap.org/themes/openweathermap/assets/img/logo_white_cropped.png)](https://openweathermap.org/api)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://openweathermap.org/api)

Vue_weather app is a cloud-enabled, mobile-ready compatible,
Vue.js-powered java project.
## Features

- Current Weather Status
- Search Cities to finf weather status
- Temprature

## Installation

This Project requires [Vue.js](https://vuejs.org/) v3+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd vue-wr
npm install
npm run serve
```

For production environments...

 vue-wr

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


###Main Script

<script>
export default {
  name: "Home",
  data() {
    return {
      api_key: "Your_Api_Key",
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

## License

MIT

**Free Software, Hell Yeah!**

