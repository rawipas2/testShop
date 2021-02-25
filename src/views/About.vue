<template>
  <div class="about">
    <v-card>
      <v-card-text>
        <v-card-title>
          รายการสินค้า
        </v-card-title>
        <v-row
        v-for="(item,index) in listCart"
        :key="index"
        >
          <v-col>
            {{item.title}}
          </v-col>
          <v-col>
            {{item.price}} บาท
          </v-col>
        </v-row>
      </v-card-text>
      <v-card-actions>
       <v-row>
         <v-col>
           ราคารวม :
         </v-col>
         <v-col>
           {{sum}}
         </v-col>
       </v-row>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ['listCart'],
  data() {
    return {
      sum: 0
    }
  },
  methods: {
    sumPrice(){
      this.listCart.forEach(element => {
        this.sum = this.sum + element.price
      });
    }
  },
  created() {
    this.sumPrice()
  }
}
</script>
