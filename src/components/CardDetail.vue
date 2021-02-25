<template>
  <div>
    <v-card>
      <v-card-text>
        <v-row>
          <v-col>
            <v-img
                :src="item.image"
                />
          </v-col>
          <v-col>
            <v-row>
              <v-col>
                <v-row>
                  <v-col cols="auto">
                    <v-btn
                    @click="addToCart"
                    > เพิ่มไปยังรถเข็น </v-btn>
                  </v-col>
                </v-row>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  props: ["item"],
  data() {
    return {
      unit: 0,
    };
  },
  methods: {
      addToCart() {
          let catagory = {
            "title" : this.item.title,
            "price" : this.item.price
          }
          this.$emit('addToCart', catagory)
      }
  }
};
</script>