<script>
// import { reactive } from 'vue'
import axios from 'axios'
export default {
    name : 'Home',

    // composition vue
    // setup() {
    //     let data = reactive({
    //         city : '',
    //         weather : null
    //     })
        
    //     const apiUrl = 'https://api.openweathermap.org/data/2.5/weather'
    //     const apiKey = 'ceacd8d818381103aab0d218edbd4c55'
    //     const getWeather = () => {
    //         axios(`${ apiUrl }?units=metric&q=${ data.city }&appid=${ apiKey }`)
    //         .then(response => {
    //             data.weather = response.data
    //             console.log(response);
    //         })
    //     }

    //     return {
    //         data,
    //         getWeather
    //     }
    // },

    // options vue
    data () {
        return {
            city : '',
            weather : null,
            apiUrl : 'http://localhost:3000/'
        }
    },
    methods : {
        getWeather() {
            axios(`${ this.apiUrl }?units=metric&q=${ this.city }`)
            .then(response => {
                this.weather = response.data
                console.log(response);
        }
    )}
    }
}
</script>

<template>
    <div class="home">
        <h1>Weather App</h1>
        <div class="enter-city">
            <input type="text" placeholder="Enter a city" v-model="city"><br/>
            <button @click="getWeather">Search</button>
        </div>
        <div v-if="weather" class="weather">
            <h1> Temp :{{ Math.round(weather.main.temp )}}&deg;</h1>
            <h1> Feels Like : {{ Math.round(weather.main.feels_like )}}&deg;</h1>
            <h2>Weather : {{ weather.weather[0].main }}</h2>
            <h3>Clouds : {{ weather.weather[0].description }}</h3>
        </div>
    </div>
</template>

<style>
* {
    text-align: center;
    background-image: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQkbX5TJyPXuwZF8_5BcdUgKeXuq6YcKo2ddQ&s');
}
input {
    font-size: 40px;
    color: darkseagreen;
    height: 50px;
    width: 220px;
}
::placeholder{
    color: cyan;
}
.weather {
    margin-top: 10px; 
}
h1 {
    font-size: 40px;
    color: 000;
}
button {
    font-size: 20px;
    color: darkseagreen;
    height: 30px;
    width: 80px;
    margin-top: 10px;
    margin-left: 5px;
}
</style>