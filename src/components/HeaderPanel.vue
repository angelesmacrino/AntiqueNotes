<template>
  <img src="../assets/small_paper.png" alt="">
  <div class="slotContainer">
    <slot></slot>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>

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

img {
    position:fixed;
    background-size:cover;
    margin-left: 40%;
    width: 26%;
    @include mobile {
        width:60%
    }
    @include s-tablet {
        width:50%
    }
    @include l-tablet {
        width:50%
    }
}
.slotContainer {
    position:fixed;
    background-size:cover;
    margin-left: 45%;
    margin-top: 8%;
    width: 26%;
    @include l-tablet {
        margin-top:5%
    }
    @include desktop {
        margin-top:2%;
        margin-left: 42%;
    }
    @include l-desktop {
        margin-top:2%;
        margin-left: 42%;
    }
}
</style>