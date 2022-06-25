<template>
  <div id="app">
<main>
  <div class="search-box">
    <input type="text" class="search-bar" placeholder="search..."/>
  </div>
</main>
  </div>

</template>

<script>
export default {
  name: 'app',
  data () {
    return { //object
      api_key: '896bcef6e113845505149836504d38ea'
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

/* main component */
#app {
  /* background image */
  background-image: url('./assets/winter.jpg');
  /* Scales the image (while preserving its ratio) to the smallest possible size to fill the container  */
  background-size: cover;
  /*  sets the initial position for each background image. */
  background-position: bottom;
}
</style>
