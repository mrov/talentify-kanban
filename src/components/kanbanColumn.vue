<template>
    <v-col lg="3" style="min-height: 500px; background-color: #E9EAEF;">
        <div v-if="!editTitle" class="d-flex justify-center align-center mt-4">
            <h2 class="text-center">{{columnTitle}}</h2>
            <v-icon @click="editTitle = true" class="pointer ml-3" color="gray">mdi-pencil</v-icon>
        </div>
        <div v-else class="d-flex justify-center align-center mt-4 mx-4 px-3 white elevation-2">
            <v-text-field
            v-model="columnTitle"
            label="Titulo da coluna"
            single-line
            ></v-text-field>
            <v-icon @click="editTitle = false" class="pointer ml-3" color="green">mdi-check</v-icon>
        </div>
        <v-row>
            <v-col lg="12" class="pt-0">
                <kanbanCard v-for="(item, index) in items" :key="index" 
                :propDescription="item.title"
                :index="index"
                @cancel="cancelCard($event)"
                @confirm="renameCard($event)"/>
            </v-col>
        </v-row>
        <v-row>
            <v-col lg="12" class="d-flex justify-center align-center">
                <v-btn @click="addItem()" class="mb-3" small fab color="#f9770c">
                    <h1 style="color: white;">+</h1>
                </v-btn>
            </v-col>
        </v-row>
    </v-col>
</template>

<script>
import kanbanCard from '@/components/kanbanCard'
export default {
    name: 'kanbanColumn',
    data () {
        return {
            columnTitle: 'Titulo da coluna',
            editTitle: false,
            items: [{title: 'Moabe Renato'}]
        }
    },
    components: {
        kanbanCard
    },
    methods: {
        addItem () {
            this.items.push({title: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut tempor purus non venenatis hendrerit. Etiam semper odio sed eros porta efficitur. Praesent in molestie libero, eu vestibulum metus. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Maecenas ullamcorper imperdiet tempus. '})
        },
        // cardInfos = { title: String, index: indice }
        renameCard (cardInfos) {
            this.items[cardInfos.index] = ({ title: cardInfos.title })
        },
        cancelCard (cardIndex) {
            console.log(cardIndex)
            this.items.splice(cardIndex, 1)
        }
    }
}
</script>

<style lang="css">
    
</style>