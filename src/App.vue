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
</style>
