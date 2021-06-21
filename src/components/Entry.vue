<template>
    <div>
        <div class="card-body"> 
           <h5 class="card-title">TODO #{{idinfo+1}}</h5> 
            <h6 class="card-subtitle mb-2 text-dark">ID: {{entries[idinfo].id}} || gepl. Aufwand {{entries[idinfo].aufwand}} Min.</h6>
            <p class="card-text">{{entries[idinfo].message}}</p> 
            <div
            v-if="!entries[idinfo].updated"       
            >
                <button
                class="btn" 
                @click="remove()"
                >
                Löschen
                </button>

                <button 
                class="btn" 
                @click="update()"
                >
                Bearbeiten
                </button>
            </div>

            <div
            v-if="entries[idinfo].updated"
            >
                <input 
                v-model="entries[idinfo].message"
                >
                Aufwand
                <input
                style="width:50px;"
                type="number"
                v-model.number="entries[idinfo].aufwand"
                > 
                <button
                class="btn" 
                @click="addToUpdate"
                >
                Änderungen übernehmen
                </button> 
            </div>
        </div>
    </div>
</template>

<script>
import {entries} from '../data.js';

    export default {
        name: 'Entry',

        props: ['idinfo'],


        data() {
          return {entries}
        },

        methods: {
            
            remove: function(){
            return this.entries.splice(this.idinfo, 1);
            },

            update (){
            this.entries.forEach(entry => {
                entry.updated = false;
                })
            entries[this.idinfo].updated=true;
            },

            addToUpdate(){
                this.entries.forEach(entry => {
                entry.updated = false;
                })
            },

            // created() {
            //     console.log('TEST');
            //     this.$emit('updateAll', this.entries);
            // }
        }
        
    }
</script>

<style scoped>
.card-body{
    background-color: rgb(121, 216, 245);
    width: 400px;
    text-align: center;
    float: left;
    margin-top: 10px;
    margin-left: 10px;
    margin-right: 10px;
    margin-bottom: 10px;
    color: white;
    border-style: double;
    border-color: rgb(153, 153, 170);
    border-width: thick;
    border-radius: 12px;
}
.btn{
    background-color: rgb(143, 153, 175);
    color: white;
    border-radius: 5px;
    margin: 5px;
}

</style>