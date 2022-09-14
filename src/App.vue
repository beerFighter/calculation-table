<template>
  <div class="wrapper page">
    <form class="calc-form-container" @submit.prevent :class="{show: show === false}">
      <div>
        <div>
          <input id="name"
          :value="height"
          @input="height = $event.target.value"
          type="number"
          class="input-height"
          placeholder="Высота в см"
          >
        </div>

        <div >
          <input id = "name2"
          :value="width"
          @input="width = $event.target.value"
          type="number"
          class="input-width "
          placeholder="Ширина в см"
          >
        </div>
        
        <div >
          <input 
          :value="count"
          @input="count = $event.target.value"
          type="number"
          class="input-count "
          placeholder="Кол-во"
          >
        </div>

        <div >
          <input 
          :value="price"
          @input="price = $event.target.value"
          type="number"
          class="input-price"
          placeholder="Цена за ткань m^2"
          >
        </div>
        <button 
        class="btn"
        @click="createPost()"
        >Добавить</button>

      </div>
    </form>
    <hello-world :array="array"/>
    <footer>
    <div>
      <button @click="change()">
      Show
      </button>
    </div>
    </footer>
  </div>
  

</template>

<script>
import HelloWorld from "@/components/HelloWorld.vue"

export default {
  components: {
    HelloWorld
  },
  name: 'App',
  data() {
    return {
      height: '',
      width: '',
      price: '',
      count: '',
      array: [

      ],
      show: true,
    }
  },
  methods: {
    createPost() {
      
      const newTable = {
        id: Date.now(),
        height: this.height,
        width: this.width,
        count: this.count,
        price: this.price,
        An: (((this.width * this.height) / 100 ) * this.count) * this.price
      }

      this.array.push(newTable)
      this.height = ""
      this.width = ""
      this.count = ""
      this.price = ""

    },

    change() {
      this.show = !this.show
    }
  }
}
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Overpass:wght@300&display=swap');
#app {
  font-family: 'Overpass', sans-serif;
}
body {
  height: 100%;
}
.wrapper {
  min-height: 100%;
  display: flex;
  flex-direction: column;
}
.calc-form-container{
  flex: 1 1 auto;
}
.input-height, .input-width, .input-count, .input-price{
  margin: 10px 5px;
}
.show {
  display: none;
}

.btn {
  margin: 10px 0 20px 0;
}

$main-color: #F44336;
$secondary-color: rgb(0, 0, 0);
$main-color: #333;
$secondary-color: #2196f3;
$width: 200px; // Change Me

* {
  box-sizing: border-box;
}

// body {background: $main-color;}

.centered {
  width: $width;
  height: $width/5;
  margin: auto;
  position: absolute;
  top: 0; bottom: 0;
  left: 0; right: 0; 
}

.group {
  width: 100%;
  height: $width/5;
  overflow: hidden;
  position: relative;
}



input {
  display: block;
  width: 100%;
  padding-top: $width/15;
  border: none;
  border-radius: 0; // For iOS
  // border-bottom: solid $width/150 rgba(white, .5);
  color: rgb(0, 0, 0);
  font-size: $width/15;
  transition: .3s ease;

  &:focus {
    outline: none;

    ~ .bar:before {
    transform: translateX(0);
    }
  }

  // Stop Chrome's hideous pale yellow background on auto-fill
  
  &:-webkit-autofill {
    -webkit-box-shadow: 0 0 0px 1000px inset;
    -webkit-text-fill-color: white !important;
    // border-bottom-color: rgba(white, .5);
  }
}

.bar {
  // background: $secondary-color;
  background: rgba(white, .5);
  content: '';
  width: $width;
  // height: $width/100;
  height: $width/150;
  // transform: translateX(-100%);
  transition: .3s ease;
  // margin-top: -2px;
  //
  position: relative;
  &:before {
    content: '';
    position: absolute;
    width: 100%;
    height: 150%;
    background: $secondary-color;
    transform: translateX(-100%);
    
  }
}

::selection {background: rgba($secondary-color, .3);}
</style>
