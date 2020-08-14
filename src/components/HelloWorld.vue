<template>
    <div class="hello">
        <!-- <h1>Your IP is {{ ip }}</h1> -->

        <div>
            <select v-model="user.country" @change="computeState($event)">
                <option v-for="country in countries" :key="country.id"> {{ country.name }}</option>
            </select>
            <select v-if="user.country !== ''" v-model='user.state'>
                <option v-for="state in states" :key="state.id"> {{ state.name }}</option>
            </select>
            <!-- <select >
                <option v-for="state in states" :key="id"> {{ country }}</option>
            </select> -->
        </div>
        <!-- <input type="text" v-model="input.firstname" placeholder="Country" /><br /><br />
        <input type="text" v-model="input.lastname" placeholder="State" /><br /><br />
        <input type="text" v-model="input.lastname" placeholder="City" /><br /><br />
        <button>Send</button>
        <br />
        <br />
        <textarea>{{ response }}</textarea> -->
    </div>
</template>
<script>
   import axios from "axios";

    export default {
        name: 'HelloWorld',
        data () {
            return {
                countries: [
                    {name: '...'},
                ],

                states: [
                    {name: '...'},
                ],

                cities: [
                    {name: '...'},
                ],

                user: {
                    country: '',
                    state: '',
                    city: ''
                }
                // ip: "",
                // input: {
                //     firstname: "",
                //     lastname: ""
                // },
                // response: ""
            }
        },
        // beforeCreate(){
        //     var $this = this;
        //     axios.get('https://raw.githubusercontent.com/dr5hn/countries-states-cities-database/master/countries%2Bstates%2Bcities.json')
        //     .then(res => $this.countries = res.data)
        // },
        beforeCreate() {
            // var $this = this;
           axios.get('https://raw.githubusercontent.com/dr5hn/countries-states-cities-database/master/countries%2Bstates%2Bcities.json').then(response => (this.countries = response.data).catch(err => console.error(err))

            )

            // console.log(countries)

        },
        methods: {
          computeState ($event){
            const selectedCountry = $event.target.value;
            if (selectedCountry !){
                //
            }
          }
         }
    }
</script>

<style scoped>
    h1, h2 {
        font-weight: normal;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }

    textarea {
        width: 600px;
        height: 200px;
    }
</style>
