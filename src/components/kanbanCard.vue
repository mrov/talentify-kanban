<template>
    <div class="d-flex align-center elevation-1 white text-center lighten-3 py-3 px-3 mx-4 my-4">
        <div v-if="display" class="d-flex justify-space-between w-100">
            <p class="mb-0 body-1 gray--text">{{description}}</p>
            <div class="d-flex">
                <v-icon @click="display = false" class="pointer" color="gray">mdi-pencil</v-icon>
                <v-icon icon class="pointer ml-3" color="red" @click="cancelCard()">mdi-delete</v-icon>
            </div>
        </div>
        <div class="w-100" v-else>
            <v-text-field
                v-model="description"
                label="Descreva o card"
                solo
            ></v-text-field>
            <div class="d-flex justify-space-between">
                <v-btn small @click="cancelCard()">Cancelar</v-btn>
                <v-btn small color="green accent-3 white--text" @click="saveCard()">Confirmar</v-btn>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'kanbanCard',
    data () {
        return {
            display: false,
            description: ''
        }
    },
    props: ['index'],
    methods: {
        saveCard () {
            this.display = true
            this.$emit('confirm', { title: this.description, index: this.index })
        },
        cancelCard () {
            this.$emit('cancel', this.index)
        }
    }
}
</script>

<style lang="css">
    
</style>