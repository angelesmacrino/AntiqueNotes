<template>
  <p>Angeles Macrino @ 2021 All rights reserved. Background by <a href="https://www.deviantart.com/icaramello">Icaramello on Deviantart</a></p>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Inknut+Antiqua:wght@400;500;900&display=swap');

$mobile-width: 600px;
$tablet-width: 900px;
$desktop-width: 1200px;

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



p {
    position: fixed;
    left: 50%;
    transform: translateX(-50%);
    bottom:0;
    font-family: 'Inknut Antiqua', serif;
    font-size: 0.6rem;
    color:rgb(44, 27, 5);
    @include mobile {
        width:108%;
        font-size: 0.4rem;
        padding-left: 30%;
    }
    
    @include l-tablet {
        font-size: 1rem;
        width:120%;
        padding-left:52%
    }
    @media (orientation:landscape) {
            position: fixed;
            height: 5vh;
            width: 100%;
            padding-left: 0;
            text-align: center;

    }
}
</style>