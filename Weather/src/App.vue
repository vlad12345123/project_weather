<template>
    <div id="app">
        <main>
            <center>
                <div class="search-box">
                    <input type="text" class="search-bar" placeholder="Enter city name" v-model="inputCity" @keypress="Weather" />
                </div>
            </center>

            <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
                <div class="location-box">
                    <div class="location">{{ weather.name }}</div>
                </div>

                <div class="weather-box">
                    <div class="temp">{{ Math.round(weather.main.temp) - 273 }}C</div>
                </div>

                <div class="weather-additionally-box">
                    <div class="min-max">Min|Max: {{Math.round(weather.main.temp_min) - 273 }}C | {{ Math.round(weather.main.temp_max) - 273 }}C</div>
                    <div class="humidity">Humidity: {{ weather.main.humidity }}%</div>
                    <div class="pressure">Pressure: {{ weather.main.pressure }}mm</div>
                    <div class="wind">Wind: {{ weather.wind.speed }}km/h</div>
                </div>

            </div>
        </main>
    </div>
</template>





<script>
    export default {
        name: 'app',

        data() {
            return {
                url: 'https://api.openweathermap.org/data/2.5/', key: '6787da7b9818dce19a11feb79e91ca86',
                inputCity: '', weather: {}
            }
        },

        methods: {

            Weather(c) {
                if (c.key == "Enter") {
                    fetch(`${this.url}weather?q=${this.inputCity}&appid=${this.key}`).then(result => { return result.json(); }).then(this.Info);
                }
            },

            Info(results) {
                this.weather = results;
            },

        }
    }
</script>






<style>

    body {
        font-family: 'Comic Sans MS';
    }

    #app {
        background-image: url('assets/city.jpg');
        background-position: bottom;
        background-size: cover;
    }

    * {
    margin: 0;
    padding: 0;
    }

    main {
        min-height: 100vh;
        padding: 25px;
        background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
    }

    .search-box {
        width: 50%;
        margin-bottom: 50px;
    }

        .search-box .search-bar {
            display: block;
            width: 100%;
            padding: 15px;
            font-size: 20px;
            border: none;
            outline: none;
            background: none;
            box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
            background-color: rgba(255, 255, 255, 0.5);
        }

    .location-box .location {
        color: #FFF;
        font-size: 32px;
        font-weight: 500;
        text-align: center;
        text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    }

    .weather-box {
        text-align: center;
    }

        .weather-box .temp {
            display: inline-block;
            padding: 10px 25px;
            color: #FFF;
            font-size: 160px;
            font-weight: 900;
            text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
            background-color: rgba(255, 255, 255, 0.25);
            border-radius: 16px;
            margin: 30px 0px;
            box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
        }

    .weather-additionally-box{
            text-align: center;
            color: #FFF;
            font-size: 102px;
            font-weight: 900;
            text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
            background-color: rgba(255, 255, 255, 0.25);
            border-radius: 16px;
            margin: 40px 0px;
    }

        .weather-additionally-box .min-max {
            color: #FFF;
            font-size: 48px;
            font-weight: 700;
            font-style: italic;
            text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
        }

        .weather-additionally-box .humidity {
            color: #FFF;
            font-size: 48px;
            font-weight: 700;
            font-style: italic;
            text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
        }
           .weather-additionally-box .pressure {
            color: #FFF;
            font-size: 48px;
            font-weight: 700;
            font-style: italic;
            text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
        }

        .weather-additionally-box .wind {
            color: #FFF;
            font-size: 48px;
            font-weight: 700;
            font-style: italic;
            text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
        }


</style>

