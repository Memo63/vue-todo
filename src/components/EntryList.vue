<template>
    <div class="head">
         <!-- v-on:updateAll="updateEntries($event)" -->
     <h3>Anzahl ToDo's: {{count}}</h3>
        <h4 >Gesamtaufwand eingeplant: {{totalInput}} Minuten</h4>
        <Entry
        v-for="(entry, index) in entries"
        :key="index"
        :idinfo=index
        />

        <div class="input">
            Text: 
        <input
        v-model="message"
        >
        
            Aufwand
            <input
            style="width:50px;"
            type="number"
            v-model.number="aufwand"
            > 
            <button
            class="btn" 
            @click="addNewEntry"
            >Neuer Eintrag
            </button>
        </div>

    </div>
</template>

<script>

import Entry from './Entry'

import {entries} from '../data.js';


    export default {
        name: 'EntryList',

        data() {
            return {
                entries,
                message: '',
                aufwand: 0
                } 
        },

        computed: {
            count: function() {
                return this.entries.length;

            },

            totalInput: function() {
                console.log(this.entries);
                return this.entries.reduce(function(sum, item){1
                    // console.log('Summe:' + sum);
                    // console.log('Aufwand:' + item.aufwand);
                    // console.log(sum + item.aufwand);
                    return sum + item.aufwand;
                },0)
            },
        },

        methods: {
   
            addNewEntry(){
                this.entries.push({id: this.entries.length, message: this.message, aufwand: this.aufwand, updated: false});
            }
        },

        components: {
            Entry    
        }
    }
</script>

<style scoped>

.btn{
    background-color: rgb(143, 153, 175);
    color: white;
    border-radius: 5px;
    margin: 5px;
}
.input{
    background-color: rgb(121, 216, 245);
    float: left;
    width: 500px;
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

</style>