<template>

    <nav class="navBar">
        <div class="empty"></div>
        <ul class=navLinks>
            <li @click = "Tooltip('showHelp')">Help</li>
        </ul>
    </nav>
    <div id="headerWrapper" :class="{'open':showToolTip, 'closed':!showToolTip}">
        <HeaderPanel >
            <p>Click on the <span><img src="../assets/quill.svg" alt="quill symbol"></span> symbol to write a new note. You have a maxium of 
                10 notes and each note has a maximun of 300 characters</p>
            <p>Click on the <span><img src="../assets/cross.svg" alt="x symbol"></span> symbol to delete a note.</p>
        </HeaderPanel>

    </div>
    
    
</template>

<script>
import HeaderPanel from "./HeaderPanel.vue"
export default {
    components: {
        HeaderPanel
    },
    data() {
        return {
            showToolTip: false,
            activeSection : []            
        }
    },
    methods: {
        Tooltip(section) {
            this.showToolTip = !this.showToolTip
            this.activeSection[0] = section
            
        }
    }
}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Inknut+Antiqua:wght@400;500;900&display=swap');

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
.navBar {
    display: flex;
	flex-direction: row;
	justify-content: space-around;
        .empty {
            margin: 0;
            text-align: center;
            padding: 10px 15px;
            display: block;

        }
        .navLinks {
            margin: 0;
            padding: 0;
            list-style: none;
            margin-top: 5px;
            padding: 10px 15px;
            text-align: center;
            display:block;
            @include desktop {
                    padding: 10px 25%;
                }
            @include l-desktop {
                    padding: 10px 35%;
                }
        }
        li {
            display: inline;
            margin-left:20%;
            font-family: 'Inknut Antiqua', serif;
            color:rgb(44, 27, 5);
            cursor: pointer;

                @include s-tablet {
                    font-size: 1.5rem;
                }
                @include l-tablet {
                    font-size: 1.5rem;
                    margin-left:30%;
                    padding-left:10%
                }
                @include desktop {
                    font-size: 1.6rem;
                }
                @include l-desktop {
                    font-size: 1.6rem;
                }

        }
        
}
.open {
  transition: 0.5s transform cubic-bezier(.11,.34,.65,.95);

}
.closed {

    transform: translateY(-500px);
    transition: 0.5s transform cubic-bezier(.11,.34,.65,.95);
}

#headerWrapper {
    p {
        font-family: 'Inknut Antiqua', serif;
        line-height: 1;
        font-size: 0.6rem;
        width:190%;
        color:rgb(44, 27, 5);
        @include s-tablet {
        font-size: 1rem;
        width: 150%
        }
        @include l-tablet {
        font-size: 1.8rem;
        width: 150%
        }
        @include desktop {
        font-size: 1rem;
        width: 90%
        }
        @include l-desktop {
        font-size: 1.2rem;
        width: 90%
        }
    }
    img {
        width:10px;
        color:rgb(44, 27, 5);
        @include s-tablet {
        width: 15px
        }
        @include l-tablet {
        width: 20px
        }
        @include desktop {
        width: 20px
        }
        @include l-desktop {
        width: 20px
        }
    }
}


</style>
