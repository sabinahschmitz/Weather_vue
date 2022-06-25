<template>
  <div id="app">
<main>
 <!-- v-model: creates a two way binding on a form input element or compnents -- binds it to the data elemt query -->
<!-- at keypress it's going to fetch the weather (function within methods) -->
  <div class="search-box">
    <input 
    type="text" 
    class="search-bar" 
    placeholder="search..."
    v-model="query"
    @keypress="fetchWeather" 
    />
  </div>

  <div class="weather-wrap" v-if ="typeof weather.main != 'undefined'">
    <div class="location-box">
      <div class="location">{{weather.name}}, {{weather.sys.country}}</div>
      <div class="date">Saturday 25 June 2022</div>
    </div>

    <div class="weather-box">
      <div class="temp"> {{Math.round(weather.main.temp)}}</div>
      <div class="weather">{{weather.weather[0].main}}</div>
    </div>
  </div>
</main>
  </div>

</template>

<script>
export default {
  name: 'app',
  data () {
    return { //object
      api_key: '34f6147fb63fca2fd41a930bdc18e9d6',
      url_base:'https://api.openweathermap.org/data/2.5/',

      // to bind the search box we need a query
      query: '',

      // somewhere to store the weather from the data we get back
      weather: {}
    }
  },
  // methods - somewhere to actually store the information
  methods: {
    fetchWeather (e) {
      // we dont want this function to be activated when "any key" is pressed. only when the enter key is pressed
      if (e.key =="Enter") {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`) //template string - q stands for query
          .then(res => {
            return res.json();
          }).then(this.setResults);
      }
    },
    setResults (results) {
      this.weather = results;
    },
    dateBuilder () {
      let d = new Date();
      let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[d.getDay()];
      let date = d.getDate();
      let month= months[d.getMonth()];
      let year = d.getFullYear();

      return `${day} ${date} ${month} ${year};
    }
  }
  
}
</script>



<style>

*{
  /* margin zero brings the search box all the way to the edge */
  margin: 0;
/* padding zero takes all the spacing away from the search box */
  padding: 0;
  /* tells the browser to account for any border and padding in the values you specify for an element's width and height. */
  box-sizing: border-box;
}

body {
  font-family: 'montserrat', sans-serif;
}

/* central component */
#app {
  /* background image */
  background-image: url('./assets/winter.jpg');
  /* Scales the image (while preserving its ratio) to the smallest possible size to fill the container  */
  background-size: cover;
  /*  sets the initial position for each background image. */
  background-position: bottom;
  /* allows you to change property values smoothly, over a given duration. */
  transition: 0.4s;
}
/* styling the main content of the page */
main {
  /* fills the screen by 100% aka 100 viewport height (vh) */
  min-height: 100vh;
  /* creates a padding of the main tag from the html document */
  padding: 25px;
/* adds a gray gradient over the main content */
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0, 0, 0, 0.75));
}

/* search box */
.search-box{
  /* creates space for the search bar */
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  /* Width of the saerch bar */
  width: 100%;
  /* padding makes the search bar higher */
  padding: 15px;
  color: #313131;
  font-size: 20px;
  
/* appearance none is used to control native appearance of UI controls */
  appearance: none;
  /* removes border and outline */
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
/* background color of search bar */
  background-color: rgba(255,255,255,0.5);
  /* rounding borders of searchbar */
  border-radius: 0px 16px 0px 16px;
  transition:0.4s
}

/* The :focus CSS pseudo-class represents an element (such as a form input) that has received focus. It is generally triggered when the user clicks or taps on an element */
.search-box .search-bar:focus {
/* clearer shadow when focused on */
box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
background-color: rgba(255,255,255,0.75) ;
border-radius: 16px 16px 16px 16px;
}

/* styling location from location box */
.location-box .location {
  color: #ffff;
  font-size: 32px;
  font-weight: 300;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

/* styling date in from location box */
.location-box .date {
  color: #fff;
  font-size: 20px;
  font-style: italic;
  text-align: center;

}
.weather-box{
  text-align: center;
}

/* temperautre styling */
.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 102px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0,0,0,0.25);
  background-color: rgba(255, 255, 255, 0.25);
  /* rounding the edges of the box */
  border-radius: 16px;
  /* spacing between weather box and uppter content */
  margin: 30px;
  box-shadow: 3px 6px rgba(0,0,0,0.25)
}

/* weather status styling */
.weather-box .weather{
color: #fff;
font-size: 48px;
font-weight: 700;
text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

/* continue at 16:12min  */

</style>
