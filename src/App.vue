<template>
  <img class="background img-fluid" src="./assets/victorian_or_steampunk_paper_by_icaramello_d1rxnhx.jpg" alt="victorian paper background">
  <Header />
  <div class="MainBody">
    <div class="Notes">
      <Notes />
    </div>
  <Footer />
  </div>


</template>

<script>
import Header from "./components/Header.vue"
import Notes from "./components/Notes.vue"
import Footer from "./components/Footer.vue"


export default {
  name: 'App',
  components: {
    Header,
    Notes,
    Footer
  }
}
</script>

<style lang="scss">

$mobile-width: 600px;
$tablet-width: 900px;
$desktop-width: 1200px;
$large-desktop-width: 1800px;

@mixin mobile {
  @media (max-width: #{$mobile-width}) {
    @content;
  }
}
@mixin s-tablet {
    @media (min-width: #{$mobile-width + 1px}) and (max-width: #{$tablet-width}) {
    @content;
  }
}
@mixin l-tablet {
    @media (min-width: #{$tablet-width + 1px}) and (max-width: #{$desktop-width}) {
    @content;
  }
}
@mixin desktop {
    @media (min-width: #{$desktop-width + 1px}) and (max-width: #{$large-desktop-width}) {
    @content;
  }
}
@mixin l-desktop {
    @media (min-width: #{$large-desktop-width + 1px}){
    @content;
  }
}

@media (orientation:landscape) {
  html, body{
        height: 100%;
  }
}

html {
  background: black;
}

body {
  margin: 0px 0px 0px 0px
}

.background {
  position: absolute;
  z-index: -1;
  left: 50%;
  transform: translateX(-50%);
  height: 100vh;

  @include mobile {
            width:100%;
            height:100%
        }

  @media (max-width: #{$desktop-width}) and (orientation:landscape) {
    width:100%;
    height: 200vh
  }

}

.MainBody {
  display:flex;
  flex-direction: column;
  
    .Notes {
      min-height:40vh;
      max-height:fit-content;
      text-align:center;
    }
    .ToDo {
      text-align:center;
    }
}


</style>
