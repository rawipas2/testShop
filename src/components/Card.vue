<template>
    <div>
        <v-card
        width="250"
        @click="openDialog"
        >
            <v-card-title>
                {{item.title}}
            </v-card-title>
            <v-card-subtitle>
                {{item.subtitle}}
            </v-card-subtitle>
            <v-card-text>
                <v-img 
                height="250"
                :src="item.image"
                />
                {{item.description}}
            </v-card-text>
        </v-card>
        <v-dialog
        v-model="dialog"
        width="500"
        >
            <DialogCard 
            :item="item"
            @addToCart="addToCart"
            />
        </v-dialog>
    </div>
</template>

<script>
import DialogCard from './CardDetail'
export default {
    props: ["item"],
    components : {
        DialogCard
    },
    data() {
        return {
            dialog: false
        }
    },
    methods: {
        openDialog() {
            this.dialog = true
        },
        addToCart(e) {
            this.$emit('addToCart', e)
        }
    }
}
</script>