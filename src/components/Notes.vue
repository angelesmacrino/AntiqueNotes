<template>
  <h2>Notes <span> <img :class="{'available':numberOfNotes < 6, 'unavailable':numberOfNotes >= 6}" @click="addNote" src="../assets/quill.svg" alt=""> </span></h2>
  <div v-if="writingNote" class="writerBlock">
    <span @keydown.enter="enterNote" ref="note" class="input" role="textbox" contenteditable tabindex=-1>Write something...</span>
  </div>
  <div v-for='(note, index) in notes' :key="note">
    <p class="singleNote"> <img src="../assets/cross.svg" alt="cross symbol" v-on:click="removeNote(index)"> {{note}}</p>
  </div>
</template>

<script>
//max width de las notas y text start del escritor, estilo de error
export default {
  data() {
    return {
      numberOfNotes: 0,
      writingNote:false,
      notes: []
    }
  },
  methods: {
    addNote() {
      if (this.numberOfNotes < 6 ) {
        this.writingNote = !this.writingNote
      }
    },
    enterNote() {
      if (this.$refs.note.innerHTML != "") {
        if (this.$refs.note.innerHTML.length <= 300) {
          this.notes.push(this.$refs.note.innerHTML);
          localStorage.setItem(`${this.notes.indexOf(this.$refs.note.innerHTML)}`, this.$refs.note.innerHTML);
          this.writingNote = false;
          this.numberOfNotes++ 
        }
        else {
          alert("no puede superar los 100 caracteres")
        } 
      }
      else {
        this.writingNote = false
      }
    },
    removeNote(index) {
            //  this.notes.length = 0
      localStorage.removeItem(index);
      this.notes.splice(index,1)
      this.numberOfNotes--  
    }
  },
  mounted() {
    for (let i = 0; i < localStorage.length; i++) {
      if (localStorage[i]!=undefined) { 
        this.notes.push(localStorage[i])
      }
    }

  },
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

h2 {
  font-family: 'Inknut Antiqua', serif;
  margin-bottom:0;
  color:rgb(44, 27, 5);   
  img {
    width:18px;
  }
    }
.available {
  cursor:pointer
}
.unavailable {
  cursor:default;
  filter:contrast(0.2)
}
.writerBlock {
  display:flex;
  justify-content: start;
  .input {
    display:inline-block;
    margin-left:15%;
    margin-bottom:5%;
    max-width:80vw;
    font-family: 'Inknut Antiqua', serif;
    font-size: 0.5rem;
    color:rgb(44, 27, 5);
    background: none;
    border:none;
    border-bottom: 1px solid rgb(44, 27, 5);
    &:focus {
      outline: none;
    }
    @include mobile {
      margin-left: 15%;
    }
    @include s-tablet {
      margin-left: 15%;
    }
    @include l-tablet {
      margin-left: 15%;
    }
    @include desktop {
      margin-left: 35%;
    }
    @include l-desktop {
      margin-left: 35%;
      }
    }
  
}
.singleNote {
  width:50%;  
  margin:0 auto;
  margin-bottom:5px;
  padding-left:15%;
  text-align: start;
  color:rgb(44, 27, 5);
  @include mobile {
    width:70%;
    padding-left:0;
  }
  @include s-tablet {
    width:70%;
    padding-left:0;
  }
  @include l-tablet {
    width:70%;
    padding-left:0;
  }
  @include desktop {
    width:30%;
    padding-left:0;
  }
  @include l-desktop {
    width:30%;
    padding-left:0;
  }
}
img {
  width: 18px;
  cursor:pointer;
}
</style>

