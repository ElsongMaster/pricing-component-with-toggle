<template>
  <div class="w-screen h-screen bg-gray-100">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1 class="text-3xl font-bold text-gray-500 pt-10 mb-10">Our Pricing</h1>
    <fieldset>
      <span>Annually</span>
      <label>
        <input
          class="cb cb1"
          type="checkbox"
          name="social"
          @click="cbChange(this)"
          :checked = false
        />
        <i></i>
      </label>
      <span>Monthly</span>
    </fieldset>
    <div
      class="container flex border-red-700 w-3/4 mx-auto"
      style="border: 2px solid green"
    >
      <CardPrice
        v-for="card in tabCard"
        :key="card.titlePackage"
        :titlePackage="card.titlePackage"
        v-model:price="card.price"
        :storageCapacity="card.storageCapacity"
        :usersNb="card.usersNb"
        :sendupCapacity="card.sendupCapacity"
        :link="card.link"
        :class="card.titlePackage =='Professional'?'active-card':''"
      />

    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import CardPrice from "./components/card-price.vue";

export default {
  name: "App",
  components: {
    // HelloWorld
    CardPrice,
  },

  data() {
    return {
      tabCard: [
        {
          titlePackage: "Basic",
          price: 19.99,
          storageCapacity: "500 GB",
          usersNb: 2,
          sendupCapacity: "3 GB",
          link: "",
        },
        {
          titlePackage: "Professional",
          price: 24.99,
          storageCapacity: "1 TB",
          usersNb: 5,
          sendupCapacity: "10 GB",
          link: "",
        },
        {
          titlePackage: "Master",
          price: 39.99,
          storageCapacity: "2 TB",
          usersNb: 10,
          sendupCapacity: "20 GB",
          link: "",
        },
      ],
    };
  },
  computed:{
    priceRounded(obj){
      return obj.price.toFixed(2)
    }
  },
  methods: {
    cbChange(obj) {
      // var cb = document.getElementById("cb");
      if (obj.checked) {
        obj.checked = false;
        this.tabCard.forEach((card) => {
          card.price = Math.floor(card.price / 10)+'.99';
        });
      } else {
        obj.checked = true;
        this.tabCard.forEach((card) => {
          card.price = Math.floor((card.price * 10))+'.99';
        });
      }
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
fieldset {
  display: flex;
  justify-content: center;
  align-items: center;
}

label {
  font-family: "Montserrat", sans-serif;
  font-size: 1.2rem;
  cursor: pointer;
  display: block;
  margin: 1em;
  > input {
    display: none;
  }

  span {
    color: #6a759b;
  }

  i {
    display: inline-block;
    width: 64px;
    height: 40px;
    border-radius: 20px;
    vertical-align: middle;
    transition: 0.25s 0.09s;
    position: relative;
    background: #deeff7;
    &:after {
      content: " ";
      display: block;
      width: 30px;
      height: 30px;
      top: 5px;
      right: 5px;
      border-radius: 50%;
      background: #fff;
      position: absolute;
      box-shadow: 1px 2px 4px 0 rgba(#000, 0.4);
      transition: 0.15s;
    }
  }

  // Checked-state
  > input:checked + i {
    background: #1094fb;
  }

  > input:checked + i + span {
    color: #29316b;
  }

  > input:checked + i:after {
    transform: translateX(-25px);
  }
}
.active-card{
  background-color: rgba(106, 161, 238,0.8);
  // width: 305px; height: 65vh !important; 
  // position: relative;
  // bottom: 5%;
  scale: 1.5;
  *{
    color:white;
  }
}
</style>
