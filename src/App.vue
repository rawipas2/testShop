<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
    <v-btn @click="openHomePage">
      Home
    </v-btn>
    <v-spacer />
     <v-badge
        color="error"
        overlap
        :content="`${cartUnit}`"
      >
      <v-btn icon @click="openCart">
        <v-icon>
          mdi-cart
        </v-icon>
      </v-btn>
     </v-badge>
    </v-app-bar>

    <v-main>
      <Home 
      v-if="!cartPage"
      :cartUnit="cartUnit"
      @addToCart="addToCart"
      />

      <About 
      v-else
      :listCart="listCart"
      />
    </v-main>
  </v-app>
</template>

<script>
import Home from './views/Home'
import About from './views/About'
export default {
  components: {
    Home,
    About
  },
  data() {
    return {
      cartUnit: 0,
      listCart : [],
      cartPage: false
    }
  },
  methods: {
    addToCart(e) {
      this.cartUnit = this.cartUnit + 1
      this.listCart.push(e)
    },
    openCart() {
      this.cartPage = true
    },
    openHomePage() {
      this.cartPage = false
    }
  }
}
</script>