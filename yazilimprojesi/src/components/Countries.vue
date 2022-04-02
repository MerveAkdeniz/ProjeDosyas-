<template>
    <div>
        <div class="container">
            <input type="text" v-model="search" id="myInput" onkeyup="myFunction()" placeholder="Search for names..">

        </div>
        <br><br>
        <div class="container">
            <table class="table table-hover table-dark table-bordered table-striped" id="c">
                <thead>
                    <tr>
                        <th scope="col">NAME</th>
                        <th scope="col">CAPİTAL</th>
                        <th scope="col">REGİON</th>
                        <th scope="col">FLAG</th>
                    </tr>
                </thead>
                <tbody class="myTable">
                    <tr v-for="country in countries">
                        <td>{{country.name}}</td>
                        <td>{{country.capital}}</td>
                        <td>{{country.region}}</td>
                        <td>{{country.flag}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                countries: null,
            };
        },
        created: function () {
            axios.get('https://restcountries.com/v2/all').then(res => {
                this.countries = res.data;
                console.log(this.countries);
            })

        },



    }
</script>

<style>

</style>