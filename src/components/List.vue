<template>
    <div v-for="club in clubs" :key="club.id">
        <div>{{ club.name }}</div>
        <div>{{ club.code }}</div>
        <div>{{ club.country }}</div>
        <div>{{ club.year_of_creation }}</div>
        <div>{{ club.owner }}</div>
        <div>{{ club.coach }}</div>
        <div>{{ club.address.city }}</div>
        <div>{{ club.address.street }}</div>
        <div>{{ club.address.number }}</div>
        <div>{{ club.stadium.name }}</div>
        <div>{{ club.stadium.capacity }}</div>
        <img :src="club.img" />
        <p>-------------------------------------</p>
    </div>
</template>

<script>

import axios from 'axios';

export default {
    name: "list",
    data() {
        return {
            clubs: []
        };
    },
    created() {
        this.loadData();
    },
    methods: {
        loadData: function () {
            var vm = this;
            axios.get('https://raw.githubusercontent.com/tomasz78285/mobilnetk/main/db.json')
            .then(function (response) {
               // console.log(response.data.clubs[0].address[0].city);
                vm.clubs = response.data.clubs;
            })
            .catch(function (error) {
                vm.clubs = 'An error occured.' + error;
            });
            
        }
    }
};
</script>

<style>
</style>