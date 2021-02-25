<template>
  <div>
    <v-row>
      <v-col
      cols="auto"
      v-for="(item, index) in catagory"
      :key="index"
      >
       <CardDetail 
       :item="item"
       :cartUnit="cartUnit"
       @addToCart="addToCart"
      />
      </v-col>
    </v-row>
  </div>
</template>

<script>
import CardDetail from '../components/Card'
import CatagoryData from '../assets/catagory.json'

export default {
  name: 'Home',
  components: {
    CardDetail
  },
  props: ['cartUnit'],
  data() {
    return {
      catagory: CatagoryData,
      listCatagory: []
    }
  },
  methods: {
    addToCart(e) {
      this.listCatagory.push(e)
      this.$emit('addToCart',  e)
    }
  }
}
</script>
