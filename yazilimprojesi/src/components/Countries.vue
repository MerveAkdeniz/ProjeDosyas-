<template>
    <div>
        <div class="container">
            <input type="text" class="search" id="myInput" onkeyup="myFunction()" placeholder="Search for names..">

        </div>
        <br><br>
        <div class="container">
            <table class="table table-hover table-dark table-bordered table-striped">
                <thead>
                    <tr>
                        <th scope="col">NAME</th>
                        <th scope="col">CAPİTAL</th>
                        <th scope="col">REGİON</th>
                        <th scope="col">FLAG</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="country in countries">
                        <td>{{country.name}}</td>
                        <td>{{country.capital}}</td>
                        <td>{{country.region}}</td>
                        <td>{{country.flag}}</td>
                    </tr>
                </tbody>
                <tfoot>
                    <tr class="warning no-result" style="display:none;">
                        <td colspan="8"><i class="fa fa-warning"></i> Bulunamadı</td>
                    </tr>
                </tfoot>
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
        }
        
    }
</script>

<style>

</style>